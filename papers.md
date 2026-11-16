# 论文、白皮书与标准

> 条目格式："标题 + 来源 + 年份 + 链接 + 一句话摘要"。
>
> 🔄 **2026-11 更新**：新增经典论文 12 篇、2024—2026 新论文 6 篇、精确标准号 8 项。链接经 HTTP / WebFetch 验证；ACM 域名 403 为反爬，浏览器可正常打开。

## 学术论文

### 已有条目

| 论文 | 出处 | 摘要 |
|---|---|---|
| [OceanBase: A 707 Million tpmC Distributed Relational Database System](https://www.vldb.org/pvldb/vol15/p3385-xu.pdf) | PVLDB 15(12), VLDB 2022 | OceanBase 官方技术论文：Shared-nothing 原生分布式架构、Paxos 多数派（RPO=0, RTO<30s）、LSM-Tree 存储引擎、7.07 亿 tpmC TPC-C 细节 |
| [Spanner: Google's Globally-Distributed Database](https://research.google/pubs/spanner-googles-globally-distributed-database/) | OSDI 2012 | 全球分布式数据库奠基之作，TrueTime 全局时钟 + 跨洲强一致 |
| [F1: A Distributed SQL Database That Scales](https://research.google/pubs/f1-a-distributed-sql-database-that-scales/) | VLDB 2013 | 基于 Spanner 的分布式 SQL 数据库 |
| [In Search of an Understandable Consensus Algorithm (Raft)](https://raft.github.io/raft.pdf) | USENIX ATC 2014 | Raft 共识算法原论文，多数分布式数据库副本一致性的基础 |
| [The Tail at Scale](https://research.google/pubs/the-tail-at-scale/) | CACM 2013 | 大规模分布式系统长尾延迟治理，金融核心性能设计必读 |

### 经典论文补充（新增）

| 论文 | 出处 | 摘要 |
|---|---|---|
| [The Part-Time Parliament (Paxos)](https://lamport.azurewebsites.net/pubs/lamport-paxos.pdf) | ACM TOCS 16(2), 1998 | Paxos 原始论文，「兼职议会」寓言 |
| [Paxos Made Simple](https://lamport.azurewebsites.net/pubs/paxos-simple.pdf) | ACM SIGACT News 32(4), 2001 | 去掉寓言的简洁重述，共识算法标准入门 |
| [The Chubby lock service for loosely-coupled distributed systems](https://www.usenix.org/legacyurl/osdi-06-paper-2) | USENIX OSDI 2006 | 基于 Paxos 的分布式锁服务，GFS/Bigtable 基础，启发 ZooKeeper |
| [Paxos Made Live – An Engineering Perspective](https://www.andrew.cmu.edu/course/15-440-sp15/assets/READINGS/paxos-made-live.pdf) | ACM PODC 2007 | 从理论到生产实现 Paxos 的工程经验（Google Chubby） |
| [Consensus on Transaction Commit](https://dl.acm.org/doi/pdf/10.1145/1132863.1132867) | ACM TODS 31(1), 2006 | Gray & Lamport 用 Paxos 改造 2PC，解决阻塞问题；经典 2PC 是 F=0 特例 |
| [Percolator: Large-scale Incremental Processing Using Distributed Transactions and Notifications](https://www.usenix.org/legacy/event/osdi10/tech/full_papers/Peng.pdf) | USENIX OSDI 2010 | 基于 Bigtable 的跨行分布式事务，TiDB 事务模型源头 |
| [Zab: High-performance broadcast for primary-backup systems](https://www.cs.cornell.edu/courses/cs6452/2012sp/papers/zab-ieee.pdf) | IEEE/IFIP DSN 2011 | ZooKeeper 的原子广播协议，DSN 2021 Test-of-Time |
| [Megastore: Providing Scalable, Highly Available Storage for Interactive Services](http://www.cidrdb.org/cidr2011/Papers/CIDR11_Paper32.pdf) | CIDR 2011 | 细粒度分区内 ACID + 跨数据中心同步复制 |
| [Calvin: Fast Distributed Transactions for Partitioned Database Systems](https://cs.yale.edu/homes/thomson/publications/calvin-sigmod12.pdf) | ACM SIGMOD 2012 | 确定性事务排序消除 2PC 开销，跨分区 ACID + 异地强一致 |
| [CockroachDB: The Resilient Geo-Distributed SQL Database](https://dl.acm.org/doi/10.1145/3318464.3386134) | ACM SIGMOD **2020**（非 2016） | 弹性地理分布式 SQL，事务模型/共识复制/自动恢复 |
| [FoundationDB: A Distributed Unbundled Transactional Key Value Store](https://www.foundationdb.org/files/fdb-paper.pdf) | ACM SIGMOD 2021 | 解耦架构 KV，严格可串行化 + 确定性仿真测试 |
| [Amazon DynamoDB: A Scalable, Predictably Performant, and Fully Managed NoSQL Database Service](https://www.usenix.org/system/files/atc22-elhemali.pdf) | USENIX ATC 2022 | AWS 时隔 15 年公开的全托管 NoSQL 服务论文（注意与 2007 年 Dynamo 论文不同） |

> GoldenDB、YugabyteDB **未检索到 VLDB/SIGMOD/ICDE 等顶会系统论文**，请勿编造；可引用厂商白皮书或《金融电子化》实践文章。

### 2024—2026 新论文（新增）

| 论文 | 出处 | 摘要 |
|---|---|---|
| [TDSQL: Tencent Distributed Database System](https://www.vldb.org/pvldb/vol17/p3869-chen.pdf) | PVLDB 17(12), 2024 | 腾讯金融级分布式库：8.14 亿 tpmC / 1650 节点 / 抖动 <0.2%，8 小时压测零强制回滚零不一致（原文已核对） |
| [GaussDB: A Cloud-Native Multi-Primary Database with Compute-Memory-Storage Disaggregation](https://www.vldb.org/pvldb/vol17/p3786-li.pdf) | PVLDB 17(12), 2024 | 华为+清华：三层解耦云原生多主，页面归属迁移实现多写高吞吐 |
| [A survey on hybrid transactional and analytical processing](https://link.springer.com/content/pdf/10.1007/s00778-024-00858-9.pdf) | VLDB Journal 33(5), 2024 | HTAP 系统分类、挑战、基准与趋势综述 |
| [From Scale-Up to Scale-Out: PolarDB's Journey to Achieving 2 Billion tpmC](https://www.vldb.org/pvldb/vol18/p5059-yang.pdf) | PVLDB 18(12), 2025 | 阿里云 PolarDB 八年演进：2340 节点、TPC-C 超 20 亿 tpmC、抖动 ≤0.16% |
| [Reaching the Pinnacle of TPC-DS: Co-design of Architecture, Executor, and Storage in TDSQL](https://www.vldb.org/pvldb/vol19/p4009-chu.pdf) | PVLDB 19(12), 2026 | 腾讯分布式 OLAP：架构/执行器/存储协同设计，TPC-DS 公开榜首 |
| [Unlocking the Potential of CXL for Disaggregated Memory in Cloud-Native Databases](https://www.alibabacloud.com/help/doc-detail/2931922.html) | ACM SIGMOD 2025 工业赛道最佳论文 | 阿里云 PolarDB 基于 CXL 的池化内存，性能达 RDMA 的 2.1 倍（官方说明页；论文正文需 ACM） |

> AI4DB 方向 2025—2026 论文密集，完整清单见 [awesome-ai4db-paper](https://github.com/Wind-Gone/awesome-ai4db-paper)（已验证）。

## 白皮书 / 报告

- 中国信通院（CAICT）：
  - [《数据库发展研究报告（2025 年）》及《中国数据库产业图谱（2025）》](https://www.stdaily.com/web/gdxw/2025-07/17/content_371605.html)：2024 年中国数据库市场约 596 亿元、占全球 7.3%，宣告数据库进入「AI 原生时代」
  - 《分布式数据库运维管理实践指南（1.0）》（2024，云大所成果精编）
  - 《金融分布式架构》系列研究报告
- 金融信创生态实验室：金融信创解决方案目录与试点名单
- 厂商白皮书：
  - 蚂蚁《金融机构分布式架构白皮书》
  - 腾讯云《金融分布式数据库 TDSQL 白皮书》
  - [腾讯云《商业银行核心系统分布式转型白皮书》（2025-07）](https://www.cet.com.cn/wzsy/kjzx/10234306.shtml)：提炼 300+ 公共技术能力，含新一代银行分布式核心整体架构（已验证）
  - 华为《金融核心现代化》系列
  - 中兴通讯 GoldenDB 金融级分布式数据库白皮书
- The Forrester Wave™: Translytical Data Platforms, Q4 2024：15 家厂商入选，PingCAP、OceanBase 为中国仅有的两家（中文报道可访问，原报告需订阅）
- IDC / Gartner：Core Banking Platforms 厂商评估（MarketScape / Magic Quadrant），多数需注册或付费

## 行业标准 / 监管文件（新增精确条目）

| 标准 / 文件 | 发布机构 | 年份 | 链接 | 说明 |
|---|---|---|---|---|
| **JR/T 0203—2020**《分布式数据库技术金融应用规范 技术架构》 | 人民银行 / 全国金融标准化技术委员会 | 2020 | [标准详情](https://hbba.sacinfo.org.cn/stdDetail/c2000ea77b705d70148114281470a06f2112f605fd0f79d487a8b51fff930a9f) | 金融分布式事务数据库架构要求（银发〔2020〕285 号发布） |
| **JR/T 0204—2020**《分布式数据库技术金融应用规范 安全技术要求》 | 人民银行 | 2020 | [标准详情](https://hbba.sacinfo.org.cn/snDetail/4f265a881c7a5aa09141c75e227ac4b8394b41172e274d476709cfd10a109368) | 金融分布式数据库安全技术要求 |
| **JR/T 0205—2020**《分布式数据库技术金融应用规范 灾难恢复要求》 | 人民银行 | 2020 | 同上发布页 | 金融分布式数据库灾难恢复能力要求 |
| **JR/T 0184—2020**《金融分布式账本技术安全规范》 | 人民银行 | 2020 | [标准详情](https://www.ndls.org.cn/standard/detail/75160a5a3d60cd7079c19bd33583a073) | 共识协议、智能合约、隐私保护、监管支撑（注：仓库旧版误记为 JR/T 0192，已更正） |
| **SJ/T 11938—2024**《安全可靠 分布式事务型数据库技术要求》 | 工信部 | 2024 | [标准详情](https://std.samr.gov.cn/hb/search/stdHBDetailed?id=2001053ADF142057E06397BE0A0A0A87) | 信创方向，2024-10-01 实施 |
| **SJ/T 11939—2024**《安全可靠 集中式事务型数据库技术要求》 | 工信部 | 2024 | [标准详情](https://hbba.sacinfo.org.cn/snDetail/8360faa3254c2826cfcadb9a12a3e5bbc9b3bfd7f602de2a1735feb7de344ac7) | 与 11938 同批（工信部公告 2024 年第 18 号） |
| 《金融科技发展规划（2022—2025 年）》 | 人民银行 | 2022 | [央行原文](https://www.pbc.gov.cn/goutongjiaoliu/113456/113469/2025092212552393945/index.html) | 金融数字化转型总体思路、6 大目标、8 项重点任务 |
| 《商业银行信息科技风险管理指引》（银监发〔2009〕19 号） | 原银监会 | 2009 | [PDF](https://fgw.sh.gov.cn/cmsres/2d/2d063f8237cf4cb4a1241e06c2b13bb3/88b84d8ae543d20e9508699cbe561405.pdf) | 信息科技治理、风险管理与业务连续性基础文件，现行有效 |

> GB/T 38664—2020《信息技术 数据库 分布式数据库系统通用技术要求》可在[全国标准信息公共服务平台](https://openstd.samr.gov.cn/)按标准号检索，未找到稳定详情页链接。

## 会议 / 期刊

- 《金融电子化》杂志（[fcmag.com.cn](https://www.fcmag.com.cn/)）：银行业信息化官方期刊，核心改造案例主阵地
- 《中国金融电脑》：常有银行架构负责人署名长文（如工行核心转型，见 [cases.md](cases.md)）
- 技术大会：QCon / ArchSummit 金融科技专场、OceanBase DevCon、TiDB DevCon、DTCC（中国数据库技术大会）

## 延伸阅读建议

1. 先读 **Spanner 论文**建立「分布式数据库为什么能强一致」的直觉
2. 再读 **OceanBase VLDB 2022** 看工业界如何落地到金融核心场景
3. 对照 **Raft / Paxos** 理解 Multi-Raft 的工程细节
4. 用 **TDSQL / GaussDB PVLDB 2024** 对比国产库的不同系统设计取舍
5. 做迁移方案时先读 **JR/T 0203/0204/0205** 三项金融行业标准
