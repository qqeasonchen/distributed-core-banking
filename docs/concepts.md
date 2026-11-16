# 核心概念与理论基石

> **本文定位**：讲清"是什么 / 为什么"，即核心银行系统与分布式系统的基础理论和概念模型。
> 具体**银行案例**见 [cases.md](../cases.md)，**数据库产品**见 [databases.md](../databases.md)，
> **厂商**见 [vendors.md](../vendors.md)，**政策文号与时间线**见 [papers.md](../papers.md) / [timeline.md](../timeline.md)。
> 本文只保留概念与原理，不复述上述文档中的案例、数字、时间与产品版本。

## Core Banking（核心银行系统）

银行用来支撑最基础业务运转的后台系统，本质是一个**全行统一的复式账本 + 交易处理引擎**。

### 功能范围

- **客户与账户管理**：客户信息（CIF）、账户生命周期
- **存款 / 贷款**：开户、计息、结息、还款计划
- **支付结算**：转账、清算、代收代付
- **总账与会计**：所有交易入账，产出日终账务与报表

### 关键特征

| 特征 | 说明 | 背后的理论约束 |
|---|---|---|
| 集中性 | 全行统一一套账 | 单一记账主体，避免双重记账 |
| 7×24 运行 | 实时交易 + 日终批处理 | 联机与批量的一致性问题 |
| 强一致 | 余额、账务绝对准确 | 线性一致性 / 可串行化（见下文） |
| 高可用 | 宕机即全行停摆 | CAP 的可用性约束（见下文） |

### 概念辨析

- Core Banking ≠ 手机银行 / 网银（后者是**渠道层**）
- Core Banking ≠ 信贷 / 反洗钱系统（**外围专业系统**，通过接口对接）
- "分布式核心"≠ 所有层都分布式：账务的强一致单元内部仍是集中式逻辑，分布式体现在应用微服务化、数据分片多副本、基础设施池化三层

## 复式记账：银行账本的数学原理

理解银行核心，先要理解它处理的对象——**账**，而不是"数据库表"。现代银行账本源自 1494 年卢卡·帕乔利（Luca Pacioli）系统化的**复式记账法**。

### 会计恒等式（核心不变量）

```
资产 = 负债 + 所有者权益        (Assets = Liabilities + Equity)
```

每一笔交易都记作**金额相等、方向相反**的两条记录（借 Debit / 贷 Credit），因此恒等式永远成立。这带给核心系统一个极其宝贵的性质：

> **账务正确性可由数学不变量校验**——"有借必有贷，借贷必相等"。这就是"总分核对""账证核对"之所以能自动化的根本原因，也是分布式核心必须守住的单笔 ACID 底线。

### 借贷的方向语义

| 账户类型 | 借方（Dr） | 贷方（Cr） |
|---|---|---|
| 资产 | 增加 | 减少 |
| 负债 | 减少 | 增加 |
| 收入 | 减少 | 增加 |
| 费用 | 增加 | 减少 |

- 客户**存款**：银行视角负债增加 → 贷记客户存款账户；同时资产（现金/存放央行）增加 → 借记资产科目
- 客户**取款**：方向相反
- 银行对账单上的"借/贷"与记账主体视角**互为镜像**——这是核对时最容易混淆的地方

来源：[Double Entry Bookkeeping — Debit and Credit](https://www.double-entry-bookkeeping.com/bookkeeping-basics/debit-and-credit/)、[Double-entry bookkeeping (Wikiwand)](https://www.wikiwand.com/en/articles/Double-entry_bookkeeping_system)。

## CAP 定理与 PACELC：分布式的物理边界

### CAP 的精确定义（而非"三选二"）

Eric Brewer 于 2000 年提出猜想，Seth Gilbert 与 Nancy Lynch 于 2002 年给出形式化证明。三要素有严格含义：

| 要素 | 精确定义 | 常见误解 |
|---|---|---|
| **C** 一致性 | 这里特指**线性一致性（linearizability）**：写完成后发起的任意读必须返回该值或更新的值 | 误以为是 ACID 的 C（可串行化），或泛指"数据正确" |
| **A** 可用性 | 每个**未故障节点**收到的请求都必须返回响应 | 误以为是运维口径的 99.99% uptime |
| **P** 分区容错 | 网络可任意丢失节点间消息 | 误以为是可选特性——现实中 P 必然发生，不可"选 CA" |

定理的真正含义：

> **分区发生时**，需要在 C 与 A 之间二选一；**无分区时**，C 与 A 可以同时满足。
> 因此"三选二"是误导性说法——准确的决策是 **分区时的 CP / AP 抉择**。

- **CP 系统**：分区时拒绝或阻塞请求，保证不返回旧值（如 etcd、ZooKeeper、HBase 严格模式）
- **AP 系统**：分区时各节点继续响应，可能产生旧值，需后续冲突消解（如 Cassandra、DynamoDB 默认配置）

Brewer 本人 2012 年的回顾文章明确承认"三选二"表述过于简化。

来源：[Gilbert & Lynch, Brewer's Conjecture and the Feasibility of Consistent, Available, Partition-Tolerant Web Services (2002)](https://www.comp.nus.edu.sg/~gilbert/pubs/BrewersConjecture-SigAct.pdf)（论文原文）、[CAP Theorem 证明与 definitions](https://www.theorempath.com/topics/cap-theorem)。

### PACELC：把"正常时期的延迟"纳入框架

CAP 只描述分区期间的行为。Daniel Abadi 于 2012 年提出 PACELC，补上了日常运行中**延迟与一致性**的权衡：

```
if there is a Partition → trade Availability vs Consistency
else (normal operation)  → trade Latency        vs Consistency
```

原因：高可用 requires 副本；一旦数据被复制，**每次更新都要在一致性与延迟之间取舍**——与是否发生分区无关。

| 分类 | 行为 | 典型系统 |
|---|---|---|
| PC/EC | 分区保一致；平时也为一致付延迟 | Spanner、HBase、ZooKeeper |
| PA/EL | 分区保可用；平时追求低延迟 | Cassandra、Dynamo（默认） |
| PA/EC | 分区保可用；平时强一致读 | MongoDB（主读配置） |

> **对银行核心的意义**：账务类操作属 CP/EC（宁可拒绝也不能错账）；历史查询类可容忍最终一致（AP/EL）——**权衡应按操作粒度选择，而非给整个系统贴标签**。

来源：[Abadi, PACELC (2012)](https://arxiv.org/abs/1204.2795)。

## 一致性模型谱系

一致性不是开关，而是**从强到弱的谱系**。越强的保证越容易编程，但代价是延迟与可用性。

```
严格一致 > 线性一致 > 顺序一致 > 因果一致 > 会话保证 > 最终一致
```

| 模型 | 保证 | 直观理解 |
|---|---|---|
| **线性一致性** Linearizability | 操作看起来在调用与响应之间的某个瞬间原子生效，且符合实时顺序 | 单寄存器像"只有一份共享内存" |
| **顺序一致性** Sequential Consistency | 所有节点看到相同的操作顺序，但顺序可与实时顺序不同 | 大家认同同一个次序即可 |
| **因果一致性** Causal | 有因果关系的操作保序，无因果关系的可乱序 | "因"必在"果"之前可见 |
| **会话保证** Session | 读己之写、单调读、单调写、写后读 | 单用户视角的连续性 |
| **最终一致性** Eventual | 若停止更新，副本最终收敛到相同值 | "迟早会一致" |

- **线性一致性**由 Herlihy 与 Wing 于 1990 年形式化，是单对象最强保证，也是 Jepsen 检测的标准
- **会话保证**通常足以覆盖面向用户的读场景：读己之写、单调读、因果读可消除绝大多数体验异常，无需为全局线性一致性付费
- 成熟数据库支持**按操作调节**一致性（如 DynamoDB 的强一致读选项、Cassandra 的 ONE/QUORUM/ALL）

来源：[Consistency Models and the CAP Theorem](https://github.com/sujeet-pro/sujeet.pro/blob/main/content/articles/consistency-and-cap-theorem/README.md)、[Consistency Guarantees](https://valery.tech/engineering/distributed-systems/guarantees)。

### 隔离级别与异常现象（ACID 的 I）

SQL-92 用三种现象定义四级隔离，但定义模糊。Atul Adya 1999 年用**依赖图**给出严格框架，Martin Kleppmann 的 Hermitage 项目据此实测各数据库：

| 现象 | 含义 | 被哪级隔离禁止 |
|---|---|---|
| **G0** 脏写 | 写写环（write cycle） | Read Uncommitted 起 |
| **G1a** 脏读 | 读到未提交事务的写 | Read Committed 起 |
| **G1b** 中间读 | 读到非最终版本 | Read Committed 起 |
| **G1c** 循环信息流 | 仅由 ww/wr 边构成的环 | Read Committed 起 |
| **P4** 丢失更新 | 两个事务读同一值后分别覆盖 | Repeatable Read 起 |
| **G-single** 读偏斜 | 恰含一条反依赖边的环 | Snapshot Isolation 起 |
| **G2-item** 写偏斜 | 读集合重叠、写集合不相交，各自提交后违反不变量 | Serializable 才禁止 |

**写偏斜（write skew）**是金融系统最需警惕的异常：两个事务都读到"还有余额"，各自写入不相交的行，单看都合法，合起来却破坏了不变量。快照隔离（SI）无法检测——因为写集合不相交。只有可串行化快照隔离（SSI）通过检测"危险结构"（两条相邻的反依赖边）来阻止。

> **厂商映射陷阱**：PostgreSQL 的 `REPEATABLE READ` 实际是快照隔离（SI），不是 ANSI 可串行化；MySQL InnoDB 的 RR 用 next-key lock 防止部分幻读，但仍允许写偏斜。**不能凭隔离级别的名字推断保证，必须实测**。

来源：[Adya 隔离级别依赖图形式化](http://aicassindra.com/blogs/databases/db_isolation_levels.html)、[Hermitage 实测项目](https://github.com/ept/hermitage)、[ANSI isolation levels 原始论文](https://www.cs.umb.edu/~poneil/iso.pdf)。

## 共识与时钟：分布式系统的两大底座

### 共识（Consensus）

共识让一组不可靠节点就某个值达成一致。所有实用算法都建立在**多数派（quorum）交集**之上：任意两个多数派必有交集，从而保证新提案能发现并延续已提交的值。

- 容忍 f 个崩溃节点需要 **2f+1** 个节点（这是紧界，不是保守估计）
- 共识解决的是**副本间的一致**；2PC 解决的是**跨参与者的原子提交**——两者层次不同，常配合使用

算法原理与选型见 [architecture.md](architecture.md) 的"共识算法"一节。

### 时钟与事件排序

分布式系统没有全局时钟，各节点物理时钟必然漂移（即使 NTP 同步也可能相差数十毫秒）。"用当前时间戳、保留最新的"这一朴素做法在跨节点时会**静默丢失数据**。

| 时钟 | 回答的问题 | 代价 | 代表系统 |
|---|---|---|---|
| **Lamport 逻辑时钟** | 因果先后 ⇒ 时间戳更小（单向） | 无法检测并发 | Raft term（类似思想） |
| **向量时钟** | 时间戳更小 ⟺ 因果先后（双向） | 每节点一项，随参与者增长 | Dynamo、Riak |
| **混合逻辑时钟 HLC** | 因果序 + 接近物理时间 | 需限定时钟偏移 | CockroachDB、MongoDB |
| **TrueTime** | 返回时间**区间** `[earliest, latest]`，配合 commit-wait 实现外部一致 | 需 GPS + 原子钟硬件 | Google Spanner |

- **Lamport 保证是单向的**：A 导致 B ⇒ L(A)<L(B)；但 L(X)<L(Y) 不代表 X 先于 Y——两个并发事件会被任意定序
- **向量时钟**能精确检测并发，代价是 O(节点数) 的元数据
- **HLC** 是现代分布式 SQL 数据库的主流选择，兼顾因果与物理时间
- **TrueTime 的核心洞察不是"原子钟"，而是"量化不确定性并等待它过去"**：Spanner 提交时特意 sleep 掉不确定窗口，换取全局顺序——时钟越精确，等待越短

来源：[Clocks and Ordering](https://hld.handbook.academy/curriculum/distributed-systems-theory/clocks-and-ordering)、[Living without Atomic Clocks (CockroachDB)](https://www.cockroachlabs.com/blog/living-without-atomic-clocks/)。

## 术语对照

| 中文 | 英文 |
|---|---|
| 核心银行系统 | Core Banking System |
| 复式记账 / 借贷记账 | Double-entry Bookkeeping |
| 会计恒等式 | Accounting Equation |
| 线性一致性 | Linearizability |
| 可串行化 / 快照隔离 | Serializability / Snapshot Isolation (SI) |
| 写偏斜 / 读偏斜 | Write Skew / Read Skew |
| 因果一致性 / 最终一致性 | Causal / Eventual Consistency |
| 分区容错 | Partition Tolerance |
| 法定人数 / 多数派 | Quorum |
| 共识 / 原子提交 | Consensus / Atomic Commit |
| 逻辑时钟 / 向量时钟 | Logical / Vector Clock |
| 混合逻辑时钟 | Hybrid Logical Clock (HLC) |
| 反依赖（读-写依赖） | Anti-dependency (rw edge) |

## 延伸阅读（理论原始出处）

- Gilbert & Lynch, [Brewer's Conjecture and the Feasibility of Consistent, Available, Partition-Tolerant Web Services](https://www.comp.nus.edu.sg/~gilbert/pubs/BrewersConjecture-SigAct.pdf), 2002
- Lamport, [Paxos Made Simple](https://lamport.azurewebsites.net/pubs/paxos-simple.pdf), 2001
- Ongaro & Ousterhout, [In Search of an Understandable Consensus Algorithm (Raft)](https://www.usenix.org/conference/atc14/technical-sessions/presentation/ongaro), USENIX ATC 2014
- Karger et al., [Consistent Hashing and Random Trees](https://www.microsoft.com/en-us/research/publication/consistent-hashing-and-random-trees-distributed-caching-protocols-for-relieving-hot-spots-on-the-world-wide-web/), 1997
- Herlihy & Wing, *Linearizability: A Correctness Condition for Concurrent Objects*, TOPLAS 1990
- Kleppmann, [*Designing Data-Intensive Applications*](https://dataintensive.net/), O'Reilly 2017 — 一致性模型与事务章节
