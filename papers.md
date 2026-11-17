# 论文、白皮书与标准

> 条目格式："标题 + 来源 + 年份 + 链接 + 一句话摘要"。链接经可达性验证；ACM 域名 403 为反爬，浏览器可正常打开。完整政策时间线见 [timeline.md](timeline.md)。

## 学术论文

### 分布式数据库与核心系统论文

| 论文 | 出处 | 摘要 |
|---|---|---|
| [OceanBase: A 707 Million tpmC Distributed Relational Database System](https://www.vldb.org/pvldb/vol15/p3385-xu.pdf) | PVLDB 15(12), VLDB 2022 | OceanBase 官方技术论文：Shared-nothing 原生分布式架构、Paxos 多数派（RPO=0, RTO<30s）、LSM-Tree 存储引擎、7.07 亿 tpmC TPC-C 细节 |
| [Spanner: Google's Globally-Distributed Database](https://research.google/pubs/spanner-googles-globally-distributed-database/) | OSDI 2012 | 全球分布式数据库奠基之作，TrueTime 全局时钟 + 跨洲强一致 |
| [F1: A Distributed SQL Database That Scales](https://research.google/pubs/f1-a-distributed-sql-database-that-scales/) | VLDB 2013 | 基于 Spanner 的分布式 SQL 数据库 |
| [In Search of an Understandable Consensus Algorithm (Raft)](https://raft.github.io/raft.pdf) | USENIX ATC 2014 | Raft 共识算法原论文，多数分布式数据库副本一致性的基础 |
| [The Tail at Scale](https://research.google/pubs/the-tail-at-scale/) | CACM 2013 | 大规模分布式系统长尾延迟治理，金融核心性能设计必读 |

### 共识、事务与分布式系统经典论文

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

### 2024—2026 前沿论文

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

## 行业标准 / 监管文件

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

### 2014—2024 政策演进

> 这一节按时间梳理驱动分布式核心改造的政策链条。每条给出**准确文号 + 发布机构 + 关键数字**，均为公开原文，可直接引用。

| 时间 | 文件（文号） | 发布机构 | 与核心改造相关的要点 |
|---|---|---|---|
| 2014-09-03 | [《关于应用安全可控信息技术加强银行业网络安全和信息化建设的指导意见》（银监发〔2014〕39 号）](https://www.pkulaw.com/chl/5a295806ca4aa41ebdfb.html?way=textRightFblx) | 银监会 + 发改委 + 科技部 + 工信部 | **行业起点文件**。目标 2019 年安全可控技术使用率 ≥75%；从 2015 年起每年 ≥15% 递增；要求「整体架构自主设计、核心应用自主研发、核心知识自主掌握、关键技术自主应用」；操作系统/数据库领域「加大探索和尝试力度」；每年 ≥5% 信息化预算用于安全可控前瞻研究。现行有效 |
| 2014-09 | 《金融业信息技术「十三五」发展规划》前期部署 | 人民银行 | 推动金融 IT 自主可控与架构转型（早期规划文件，具体文号以官方为准） |
| 2016 | 《中国制造 2025》及「十三五」国家信息化规划 | 国务院 | 信创（信息技术应用创新）战略的政策源头，国产基础软硬件替代上升到国家战略 |
| 2019-08 | [《金融科技（FinTech）发展规划（2019—2021 年）》（银发〔2019〕209 号）](https://www.pbc.gov.cn/zhengwugongkai/4081330/4081344/4081419/4081727/2025080819055758515/index.html) | 人民银行 | 「守正创新、安全可控、普惠民生、开放共赢」；6 方面 27 项重点任务；目标 2021 年建成金融科技发展「四梁八柱」；2019 年起在北京/上海等 10 省市开展金融科技应用试点 |
| 2021-12-31 | [《金融科技发展规划（2022—2025 年）》](https://www.pbc.gov.cn/goutongjiaoliu/113456/113469/2025092212552393945/index.html) | 人民银行 | 从「立柱架梁」转向「积厚成势」，提出 6 大目标 + 8 项重点任务；明确「技术架构由集中式向分布式架构转型」 |
| 2022-01 | 《关于银行业保险业数字化转型的指导意见》 | 原银保监会 | 以数字化转型推动银行业高质量发展，构建适应现代经济的数字金融新格局 |
| 2022-02 | 《金融标准化「十四五」发展规划》 | 人民银行 + 市场监管总局 + 银保监会 + 证监会 | 推进金融业信息化核心技术安全可控标准建设，完善金融数据要素标准 |
| 2022-12 | 《关于构建数据基础制度更好发挥数据要素作用的意见》（「数据二十条」） | 国务院 | 构建数据产权/流通交易/收益分配/安全治理制度，影响核心系统数据架构与要素化 |
| 2023-07 | 《银行业普惠金融业务数字化模式规范》 | 人民银行 | 普惠金融数字化的关键举措、数据管理、风控、系统支持规范 |

> 上表 2019/2022/2023 多项文件的时间、机构、要点见[新华财经政策梳理 PDF](https://f1.cnfin.com/icmp-web-static-data/resources/third-upgrade/upload/2024/03/19/20240319190837965/c42792460a884b8b941eb36c9e955ee8.pdf)（权威汇编）。金融信创一/二/三期试点扩围节奏见 [timeline.md](timeline.md)，试点名单属行业口径，未见监管原文统一发布，谨慎引用。

### 国际监管与标准

| 时间 | 文件/事件 | 机构 | 与银行核心相关的要点 |
|---|---|---|---|
| 2015-11 / 2016-01 | [PSD2《支付服务指令修正案》（DIRECTIVE 2015/2366/EU）](https://openbankingmap.com/) | 欧盟理事会 / 欧洲议会 | 2015-11 通过、2016-01 生效；强制银行向第三方开放账户数据（AIS/PIS），催生核心系统 API 化改造；2018-01 起各成员国逐步实施，2019-09 强客户认证（SCA）要求生效 |
| 2016 / 2017 | CMA 零售银行市场调查令 / OBIE 成立 | 英国 CMA / FCA | 强制 CMA9 九大银行 2018-01 起开放账户数据 API；UK Open Banking 2018-01-13 正式上线 |
| 2016 | 全球首个金融监管沙盒 | 英国 FCA | 为金融科技/银行新产品提供受控测试环境，成为各国监管范式 |
| 2018-05 | GDPR《通用数据保护条例》生效 | 欧盟 | 客户敏感数据的存储、处理、跨境流动约束，直接影响核心系统数据架构与脱敏设计 |
| 2025-11 | [ISO 20022 迁移截止](https://www.swift.com/standards/iso-20022) | SWIFT | 全球跨境支付报文向 ISO 20022 迁移完成，核心/支付系统报文格式与数据字段须适配（**日期以 SWIFT 官方最新公告为准**） |
| 2023-06 | PSD3 / FiDA 提案发布 | 欧盟委员会 | 开放银行向开放金融（Open Finance）演进，进一步扩展数据访问范围 |

### CRS：金融账户涉税信息报送（标准 / 监管合规）

> 实操解读篇：[101个国家! 监管&银行都在做! CRS!（2018-04-02）](https://mp.weixin.qq.com/s?__biz=MzIzMTk2NjAzMg==&mid=2247483930&idx=1&sn=dba6f857c3f7da485be2a5efdda62c41)。与上表 PSD2/GDPR 同属国际监管条线，但侧重账户涉税信息交换，是银行合规与报送系统设计的依据。

- CRS 即非居民金融账户涉税信息报送（通用报告标准），目标是本国居民境外未申报的信息须在本国完成纳税义务，解决仅靠单一国家难以遏制逃税的问题；报送数据主要来自银行（服务广、客户多）。
- G20 是无执行人的国家论坛，与 OECD 合作；OECD 借鉴美国 FATCA（金融账户合规法）修改形成 CRS，统一账户信息与资产标准以避免各国理解差异导致交换数据有误（如普通话对比方言）。
- 衍生品合约也属金融资产须报送，并按结算日实际价格（金融市场逐日更市、价格不断变化）。
- 消极收入指非营业收入（股权收益、衍生品收益等，"坐家收钱"）；发现消极金融机构要查控制人是否非居民，居民无需报送、非居民须报送。
- 休眠户及指定金融账户余额≤1000 美元无需报送；部分信息需客户经理手工补录（最了解客户的人）。

### 白皮书与报告

- **2014—2018**：蚂蚁《金融云与分布式架构白皮书》早期版本、微众银行「去 IOE」实践文章（见 [cases.md](cases.md)）——这一阶段白皮书主打**「去 IOE 可行性论证」**。
- **2019—2021**：信通院《分布式数据库金融应用》系列、金融信创生态实验室首批解决方案目录、腾讯云/OceanBase 金融核心白皮书集中发布——主题转为**「迁移方法论与稳定性验证」**。
- [中兴通讯参与主编《金融业数据库供应链安全发展报告（2022）》](https://www.zte.com.cn/content/zte-site/www-zte-com-cn/china/about/news/20221118c2.html)（一手，含中信/建行两地四 AZ 多地多活案例细节）。
- [沙利文 × 头豹《2021 年中国金融级分布式数据库市场报告》](https://www.toutiao.com/article/7317276548426678835)（二手转述：GoldenDB 以 28.15 分蝉联第一）。

## 会议 / 期刊

- 《金融电子化》杂志（[fcmag.com.cn](https://www.fcmag.com.cn/)）：银行业信息化官方期刊，核心改造案例主阵地
- 《中国金融电脑》：常有银行架构负责人署名长文（如工行核心转型，见 [cases.md](cases.md)）
- 技术大会：QCon / ArchSummit 金融科技专场、OceanBase DevCon、TiDB DevCon、DTCC（中国数据库技术大会）

## 按用途查阅指引

论文与标准的价值在于支撑具体决策，按目的选择阅读顺序：

| 目的 | 优先查阅 | 能得到什么 |
|---|---|---|
| **数据库选型** | TDSQL / GaussDB / OceanBase 的 PVLDB 系统论文 + 各产品 TPC-C/TPC-DS 成绩 | 用真实系统论文而非宣传材料对比架构取舍；关注论文披露的副本协议、分片、容灾 RTO 数据 |
| **核心架构设计** | OceanBase VLDB 2022、GoldenDB《金融电子化》实践文章 | 看工业界如何把分布式数据库落到金融核心，对齐 [architecture.md](architecture.md) 的方案 |
| **迁移合规论证** | JR/T 0203/0204/0205 三项行业标准 + 银监发〔2014〕39 号文 | 立项与验收材料需要引用的标准依据与政策口径 |
| **技术背书核验** | 核对论文是否真实存在（GoldenDB / YugabyteDB 无顶会系统论文，勿编造） | 避免把厂商宣传当作学术结论，引用前先验证出处 |

> **经验判断**：厂商技术论文披露的架构细节（副本协议、一致性级别、故障恢复数据）比 benchmark 数字更有选型价值；行业标准号要精确到 JR/T xxxx-xxxx，模糊引用会在合规评审中被退回。
