# 架构设计方法论

> **本文定位**：讲清"怎么设计"——分布式核心的架构原理、设计权衡与模式。
> **具体哪些银行用了什么方案**见 [cases.md](../cases.md)；**各数据库产品能力**见 [databases.md](../databases.md)；
> **厂商产品**见 [vendors.md](../vendors.md)；**具体政策文号**见 [papers.md](../papers.md)。
> 本文只讲可复用的设计方法，不复述案例、产品版本、时间与数字。

## 总体分层模型

分布式核心的通用分层（自顶向下）：

```
渠道层    手机银行 / 网银 / 柜面 / 开放 API
   ↓  集成层    企业服务总线 / API 网关 / 服务网格
   ↓  核心层    微服务：客户、账户、存款、贷款、支付、清算、总账
   ↓  数据层    分布式数据库 + 缓存 + 消息队列
   ↓  基础设施  x86 集群 / 容器平台 / 多数据中心
```

分层的意义在于**隔离变化**：渠道创新不必改核心，存储替换不必改业务逻辑。每层内部可独立演进——这正是"核心与渠道解耦"（core-agnostic）思想的结构基础。

## 微服务拆分：用 DDD 划定边界

单体拆微服务最大的风险是**拆错边界**。领域驱动设计（DDD，Eric Evans 2003）提供了判定方法。

### 战略设计：先找边界，再写代码

| 概念 | 含义 | 在核心银行中的应用 |
|---|---|---|
| **通用语言** Ubiquitous Language | 开发与客户共用的精确词汇 | "账户"在存款、信贷、清算语境下含义不同，需分别定义 |
| **限界上下文** Bounded Context | 一个模型保持一致显式的边界 | 客户信息 / 存款账务 / 支付清算各有自己的"客户"模型 |
| **上下文映射** Context Map | 上下文之间的关系 | 核心与外围系统之间常用"防腐层"隔离 |

> **判定经验法则**：如果两个团队用同一个词却指不同的东西，那就找到了一条限界上下文边界。
> 强行用一个"大客户模型"覆盖所有语境，必然产出臃肿高耦合的系统。

**上下文映射的主要模式**：

- **防腐层（Anti-Corruption Layer, ACL）**：在整洁的新模型与遗留/外部系统之间加翻译层，防止老系统的怪癖污染新模型——这是存量核心改造中最重要的模式
- **共享内核（Shared Kernel）**：多个上下文共享一小部分模型，改动需协同
- **客户-供应商（Customer/Supplier）**：上游按下游需求塑造接口
- **遵奉者（Conformist）**：直接用上游模型，放弃翻译以简化集成
- **开放主机服务 / 发布语言（OHS / Published Language）**：以标准化协议对外开放

### 战术设计：上下文内部的建模构件

- **实体 Entity**：有唯一身份与生命周期（如账户 Account）
- **值对象 Value Object**：由属性定义、不可变（如金额 Money = 数值 + 币种）
- **聚合 Aggregate**：一组对象作为数据变更的单一单元，由**聚合根**统一控制访问
- **领域事件 Domain Event**：领域中已发生的事实，用于解耦与事件驱动
- **仓储 Repository / 工厂 Factory**：封装持久化与复杂对象创建

**聚合边界的核心判据**：*"什么东西必须同时保持一致？"* 必须一起一致的放进同一聚合（如账户与其实时余额）；不必一起一致的用 ID 引用（如订单引用商品，商品价格变化不应改写历史订单）。

**事件风暴（Event Storming）**：一种工作坊式建模技术，让领域专家与开发者用彩色便签共同梳理领域事件、聚合与边界，是识别限界上下文的有效前置手段。

来源：[Domain-Driven Design (GeeksforGeeks)](https://www.geeksforgeeks.org/system-design/domain-driven-design-ddd)、[DDD in Practice: Bounded Contexts and Aggregates](http://scopeforged.com/blog/domain-driven-design-practical)、[Eric Evans — Domain Language](https://domainlanguage.com/ddd/)。

## 数据分片策略：Range、Hash 与一致性哈希

分片（sharding）决定了数据分布与扩展能力，是分布式核心的关键设计点。

### 三种基础分片方式

| 方式 | 做法 | 优点 | 缺点 |
|---|---|---|---|
| **Range（范围）** | 按主键区间切分（如 1~5000 → 节点 A） | 支持范围查询；便于按区间迁移 | 易产生热点；分布依赖 key 分布 |
| **Hash（取模）** | `hash(key) % N` | 分布均匀 | **节点数 N 变化会重排几乎所有数据** |
| **一致性哈希** | 节点与 key 映射到同一个哈希环，key 归顺时针第一个节点 | 增删节点只迁移约 `K/(N+1)` 的数据 | 需维护环元数据；实现较复杂 |

### 为什么 `hash % N` 在扩展时是灾难

从 12 个节点扩到 13 个，`hash % N` 会重排约 **12/13 ≈ 92%** 的 key——在缓存场景意味着扩容瞬间缓存大面积失效、数据库被压垮。这是一个数学问题，不是"扩容不够快"的问题。

### 一致性哈希的原理（Karger et al. 1997）

1. 把哈希输出空间视为一个环（0 ~ 2³²-1）
2. 节点按名字/地址哈希到环上；key 也哈希到环上，归属**顺时针遇到的第一个节点**
3. 新节点加入时，只接管其前驱节点的一部分区间；其他 key 原地不动
4. **虚拟节点**：每个物理节点在环上占多个位置（Dynamo 用 token），使负载更均匀、故障时负载分散到多个节点、可按容量加权

扩展后所需虚拟节点数遵循 `Θ(ε⁻² log n)` 才能把峰值/均值比控制在 `1+ε` 内。

**相关变体**：

- **Rendezvous / HRW hashing**：对每个 key 计算所有节点的权重取最大者，无需维护环，但查询 O(N)，适合小集群
- **Jump Consistent Hash**（Google 2014）：无内存、极快，但只能从编号列表末尾增删节点
- **有界负载一致性哈希**（Google 2017）：限制单节点负载上限、溢出顺时针传递，用于缓解热点 key
- **固定槽位**（如 Redis Cluster 的 16384 槽）：以槽为迁移单位，是"目标相同、机制不同"的另一条路

来源：[Consistent Hashing: The Algorithm Behind Scalable Distributed Systems](https://backendbytes.com/articles/consistent-hashing)、[Consistent and Rendezvous Hashing](https://valery.tech/engineering/distributed-systems/hashing)、[Karger et al. 1997 论文](https://www.microsoft.com/en-us/research/publication/consistent-hashing-and-random-trees-distributed-caching-protocols-for-relieving-hot-spots-on-the-world-wide-web/)、[Amazon Dynamo 论文 (SOSP 2007)](https://www.allthingsdistributed.com/files/amazon-dynamo-sosp2007.pdf)。

## 共识算法的原理与选型

共识让不可靠节点就值达成一致。掌握其**设计权衡**比记住具体 API 更重要。

### 算法谱系

| 算法 | 年份 | 模型 | 核心机制 | 特点 |
|---|---|---|---|---|
| **Paxos** (Lamport) | 1990 提出 / 2001 简化 | 对称，多 Proposer | Prepare / Accept 两阶段 + 多数派 | 理论严谨，但工程细节留白多 |
| **Multi-Paxos** | 生产优化 | 稳定 Leader | 选一次 Leader，Phase 1 跑一次，后续只跑 Phase 2 | 消息减半，但无标准规范 |
| **Zab** (ZooKeeper) | 2008 | 主备 + epoch | 原子广播，带独立恢复阶段 | 为协调服务定制，恢复语义与 Multi-Paxos 不同 |
| **Raft** | 2014 | 强 Leader | 领导者选举 + 日志复制 + 安全性，term 机制 | 可理解性优先，规范完整 |

### Paxos 与 Raft：不是对错之争，而是抽象层次之别

- **Lamport 的"Paxos Made Simple"要点**：共识的核心思想（法定人数交集迫使新轮次延续已接受的值）并不神秘；实践者遇到的复杂度来自协议未规定的周边机制
- **Raft 的贡献**不是修正 Paxos，而是**把周边机制显式化**：强 Leader、单一 term/log 心智模型、选举与复制联合设计、成员变更（联合共识）与日志压缩都写进规范
- **Chubby 团队**的 "Paxos Made Live" 论文专门列举了从算法到可用系统之间的鸿沟（日志压缩、成员变更、主租约、磁盘损坏等）

### 选型的工程判断

> 过去十年新系统普遍默认 Raft，不是因为 Paxos 不正确，而是**"正确且易实现的协议"胜过"正确但易踩坑的协议"**——微妙的 Paxos 实现 bug 曾多次导致生产事故。

- 需要理解共识机制本身 → 从单决策 Paxos 入手（算法最小）
- 需要实现生产系统 → 从 Raft 入手（规范完整）
- 维护 2014 年前的系统 → 会遇到 Paxos 术语（Spanner 用 Multi-Paxos、ZooKeeper 用 Zab）

**共识 vs 2PC**：共识维护集群内副本的一致复制日志；2PC 协调跨**独立所有权**服务的单次原子提交。两者解决不同层次的问题，在大系统中常组合使用（共识管集群内复制，2PC/TCC 管跨服务事务）。

来源：[Paxos Made Simple (Lamport, 2001)](https://lamport.azurewebsites.net/pubs/paxos-simple.pdf)、[In Search of an Understandable Consensus Algorithm (Raft, USENIX ATC 2014)](https://www.usenix.org/conference/atc14/technical-sessions/presentation/ongaro)、[Paxos/Raft/Zab 对比解析](https://learn.padho.ai/wiki/paxos-multi-paxos-zab-what-raft-simplified)。

## 分布式事务模式的设计权衡

跨服务保证一致性有多种模式，各有故障语义与适用边界。

| 模式 | 机制 | 优点 | 代价 / 陷阱 |
|---|---|---|---|
| **2PC** 两阶段提交 | 准备 + 提交，协调者驱动 | 强一致 | 协调者故障会阻塞；资源锁定时间长 |
| **3PC** 三阶段提交 | 加 CanCommit 阶段 | 降低阻塞概率 | 网络分区下仍可能不一致 |
| **TCC** Try-Confirm-Cancel | 业务层预留 + 确认/补偿 | 资金类可控，一致性好 | 每个服务要写三个接口，侵入业务 |
| **Saga** | 长事务拆成本地事务序列 + 补偿 | 适合跨组织长流程 | 无隔离性，需处理中间状态可见 |
| **事务消息 / Outbox** | 事件与业务数据在同库同事务落盘，再异步投递 | 避免"写库成功但发消息失败" | 消费端需幂等 |

**金融场景的关键分界线**：

> 资金类业务必须走 **TCC / Saga，在业务层做"冻结 + 补偿"**；不能依赖数据库层 undo log 回滚外部不可逆资源（如已发出的清算指令）。
> 核心判断是：**资金回滚是业务设计问题，不是数据库回滚问题**。
> 在 Seata 等框架中，AT 模式仅适用于可控的内部 CRUD，资金路径要用 TCC/Saga。

来源：[Saga 模式原始论文](https://www.cs.cornell.edu/andru/cs711/2002fa/reading/sagas.pdf)、[microservices.io — Strangler 与事务模式](https://microservices.io/post/refactoring/2023/06/21/strangler-fig-application-pattern-incremental-modernization-to-services.md.html)。

## 高可用与容灾的设计目标

容灾设计用两个量化指标驱动，而不是笼统谈"高可用"：

| 指标 | 含义 | 提问方式 |
|---|---|---|
| **RPO** Recovery Point Objective | 可接受丢失多少数据 | "最多丢多久的交易？" |
| **RTO** Recovery Time Objective | 可接受停机多久 | "多久必须恢复服务？" |

按 RPO/RTO 由弱到强的典型架构抽象：

- **冷备**：RPO = 小时级，RTO = 小时级（定期备份）
- **主备（异步）**：RPO = 秒级，RTO = 分钟级
- **同城双活**：RPO ≈ 0，两机房同时承载流量，但对时延敏感
- **异地多活 / 单元化**：RPO ≈ 0，按用户分片、多地同时服务，故障整单元切换

**单元化（Set 化）**的核心思想：将数据和流量按维度切分到独立单元，**单元内闭环**，故障时整体切换。其设计要点是**全局服务（如总账、参数）必须独立部署**——否则会成为跨单元的隐式耦合点。单元化不是越多越好：机器成本与**容灾能力**正相关，与单元化本身无关；单元化的价值在于把"分"变成"分而能活"。

## 设计原则索引（理论出处）

- **DDD 战略/战术设计**：Eric Evans, *Domain-Driven Design* (2003)；[Context Mapping 模式集](http://es.wikipeda.org/w/index.php?action=edit&title=Domain-driven_design)
- **一致性哈希**：Karger et al. 1997；Dynamo (2007) 的 ring + vnodes + 复制实践
- **共识算法**：Lamport Paxos (2001)；Ongaro & Ousterhout Raft (2014)
- **隔离与一致性理论**：见 [concepts.md](concepts.md) 一致性模型与隔离异常两节
- **迁移与切换模式**：见 [migration.md](migration.md)
