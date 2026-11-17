# 分布式数据库

金融核心系统分布式化的数据底座。

> 各产品的完整发展史见 [timeline.md](timeline.md)；「产品演进里程碑」一节给出 2014—2024 逐产品版本与技术跃迁的一手来源。来源标注约定同 [cases.md](cases.md)。

## 国内主要产品

| 产品 | 背景 | 特点 | 银行案例 | 官方资源 |
|---|---|---|---|---|
| **OceanBase** | 蚂蚁集团 | 原生分布式，TPC-C 7.07 亿 tpmC，兼容 MySQL/Oracle，Paxos 多数派（RPO=0, RTO<30s） | 网商银行、北京银行、多家股份行 | [文档中心](https://docs.oceanbase.com/zh) · [GitHub](https://github.com/oceanbase/oceanbase) |
| **TDSQL** | 腾讯云 | Shared-Nothing，强同步复制 RPO=0，TPC-C 8.14 亿 tpmC，Oracle 兼容度 95%-98%，2PC/XA 分布式事务 | 邮储银行新核心、张家港农商行、微众银行、农业银行（二手口径） | [产品页](https://cloud.tencent.com/product/tddbms) · [金融云开发指南](https://doc.fincloud.tencent.com/document/product/388315/7714) |
| **GaussDB** | 华为 | 分布式 + 集中式双形态，兼容 Oracle，云原生多主（存算分离） | 工行、建行、平安银行、多家股份行 | [华为云 GaussDB](https://www.huaweicloud.com/product/gaussdb.html) |
| **GoldenDB** | 中兴/金篆信科 | 面向金融交易型场景，业界首个分布式事务强一致，具备替换大/小型机能力 | 中信银行（信用卡核心 + 账务核心）、建行对私/对公/海外核心、国开行、广发银行 | [GoldenDB 官网](https://www.ztedb.com) |
| **TiDB** | PingCAP | 开源，HTAP，兼容 MySQL，Multi-Raft | 多家城商行、支付机构 | [文档](https://docs.pingcap.com/zh) · [GitHub](https://github.com/pingcap/tidb) |
| **PolarDB / PolarDB-X** | 阿里云 | 云原生存算分离，TPC-C 20.55 亿 tpmC（2025-02）；PolarDB-X 分布式、开源 | 2025 中标国内头部国有银行国产库升级 | [openPolarDB](https://www.openpolardb.com/) |
| **达梦 DM8 / DM9** | 达梦数据 | 集中式为主，2025 IDC 本地部署事务型数据库份额国产第一 | 260+ 金融机构、1000+ 核心及 A 类系统 | [官网](https://www.dameng.com) |
| **电科金仓 KingbaseES** | 太极股份控股（原人大金仓） | 兼容 Oracle/MySQL/SQL Server/Sybase，信创场景广泛 | 金融、党政、能源 | [官网](https://www.kingbase.com.cn) |
| **GBase（南大通用）** | 南大通用 | 集中式 + 分布式双线，金融业用户渗透率第一（厂商/赛迪口径） | 240+ 金融机构，泸州银行替换 Oracle + 多套 MySQL | [官网](https://www.gbase.cn) |
| **SequoiaDB（巨杉）** | 巨杉 | 分布式老牌 | 部分银行历史数据层 | [官网](https://www.sequoiadb.com) |
| **openGauss** | 华为开源 | 集中式为主，配套分布式方案 | 信创场景广泛 | [官网](https://opengauss.org/zh/) · [Gitee](https://gitee.com/opengauss) |

### 产品速记

- **OceanBase**：支付宝 100% 核心链路在跑；「三地五中心」城市级故障无损容灾；单机分布式一体化架构（4.x 起）；MaLT 大事务框架（SIGMOD 2025）已在 4.x 生产发布。
- **TDSQL**：配套迁移工具 DTS-DBbridge（Oracle/DB2 → TDSQL）；智能 DBA 工具 DBbrain；2025-09 发布 TDSQL 3.0 家族（TDSQL / TDSQL-C / TDSQL-B）+ TDAI。
- **GoldenDB**：银行基因最深——与中信银行 2014 年联合立项、5 年研发，首个在大型银行账务核心投产的国产数据库（2020）；V7 获分布式数据库安全可靠二级认证（2026-05，行业媒体口径）。
- **GBase**：泸州银行以 GBase 统一替换 Oracle 与多套 MySQL，夜间批量 2.5–3 小时 → 约 30 分钟（厂商口径）；2026-04 GBase 8s 成为国内首个通过信通院「共享存储架构数据库基础能力」测试的产品。

## 2025—2026 产品进展

| 产品 | 关键进展 | 时间 | 来源 |
|---|---|---|---|
| **OceanBase** | 官网称服务全球 4000+ 客户、开源累计下载 200 万+；IDC 中国分布式数据库本地部署及金融行业本地部署份额第一；4.4.2 LTS 集成 TP/AP/AI（湖库一体） | 2025—2026 | [官网](https://www.oceanbase.com/en) · [MaLT 技术博客](https://en.oceanbase.com/blog/28446826752)（一手，**部分融资/收入数字为二手，未收录**） |
| **TDSQL** | 2025-05 发布一体化版本（多引擎统一管控）；2025-09 TDSQL 3.0 家族；TDSQL 论文载 PVLDB 17(12)，8.14 亿 tpmC / 1650 节点 / 抖动 <0.2%（论文原文已核对） | 2024—2025 | [PVLDB 论文](https://www.vldb.org/pvldb/vol17/p3869-chen.pdf)（一手） · [TDSQL 3.0 详解](https://cloud.tencent.com/developer/article/2702142) |
| **GaussDB / openGauss** | HC2026 预告 openGauss 7.0.0 LTS：oGRAC 多写 570 万 tpmC、扩展比 >0.85、RTO<10 秒；邮储个人核心支撑 6.5 亿客户/日均 20 亿笔、结息 140 → 25 分钟 | 2026 | [墨天轮](http://www.modb.pro/db/2101982801105084416)（二手，厂商预告口径） |
| **GoldenDB** | GoldenDB V7 / Lite V7 / EBASE V3 通过安全可靠测评；2026-04 发布向量版（标量+向量+全文混合检索）；服务 1500+ 客户、近 200 家金融核心客户 | 2026 | [中兴通讯技术（2025-12）](https://www.zte.com.cn/content/zte-site/www-zte-com-cn/china/about/magazine/zte-technologies/2025/12/4/32.html)（一手，已验证） |
| **TiDB** | v8.5 为主流生产版本；浙商银行电信反欺诈 20 亿行大表查询从数十秒 → 数十毫秒；TiFlash 列存用于实时风控。**未检索到 9.x 可靠发布信息，勿写入未证实版本号** | 2025—2026 | [PingCAP 案例](https://www.pingcap.com/?p=25861/)（一手） |
| **PolarDB / PolarDB-X** | 2025-02 TPC-C **20.55 亿 tpmC**（单位成本 0.8 元、波动 0.16%）；PolarDB-X 1→1024 节点；2025 中标头部国有银行，500 节点同城 RTO≈7 秒、跨城<30 秒；开源 V2.5.0 新增 AI Function / HNSW 向量索引 | 2025—2026 | [开源社区](https://www.openpolardb.com/) · [PVLDB 18(12) PolarDB 20 亿 tpmC 论文](https://www.vldb.org/pvldb/vol18/p5059-yang.pdf) |
| **达梦数据** | 2025 营收 13.06 亿元（+25.03%）；IDC 2025 中国本地部署事务型数据库份额 14.6% 首超国外厂商（10.8%）；金融行业本地部署集中式事务库份额 16.1% 国产第一；2026-04 发布 DM9（原生向量、AI 共生） | 2026 | [达梦官网 IDC 解读](https://www.dameng.com/news/details185_190621.html)（一手，已核对） |
| **电科金仓** | KES V9 2025 新增 SQL Server / Sybase 兼容模式，累计部署超 100 万套；2026-10 发布 KESAI 数据库（库内 AI：语义定义、向量推理、安全管控） | 2025—2026 | [金仓技术博客](https://www.kingbase.com.cn/)（一手） |

## 2014—2024 产品演进里程碑

> 数据库选型不能只看当前版本——**稳定运行年限 + 版本连续性**比单次 benchmark 更能说明成熟度。以下按产品给出关键跃迁节点，均来自厂商官网/官方里程碑页（一手）。

### OceanBase（2010—2024）

| 时间 | 版本/事件 | 关键能力 |
|---|---|---|
| 2010 | 项目立项（阳振坤团队） | 首个应用淘宝收藏夹，解决高并发大表连接小表 |
| 2012 | 支持标准 SQL | 从专用 API 存储演进为通用关系型数据库 |
| 2014 | 0.5，双十一承担 10% 交易流量 | 取代 Oracle 支撑支付宝核心交易；**首次实现 RPO=0、RTO<30s** |
| 2015 | 双十一 100% 交易流量 + 网商银行上线 | 全球首个跑在银行核心账务的分布式数据库 |
| 2016 | **1.0（架构大重构）** | 对等 P2P 节点 + 真正分布式事务 + 多租户（架构沿用至今）；支付宝 100% 核心库（含账务）迁完；支付峰值 12 万笔/秒 |
| 2017 | 南京银行上线 | 首个外部客户，走出阿里/蚂蚁体系；完成蚂蚁核心最后一个 Oracle 替换 |
| 2018 | **2.0** | 完整 Oracle 兼容模式（PL/SQL、函数、类型），大幅降低迁移改造成本 |
| 2019-10 | 2.2 TPC-C **6088 万 tpmC** | 打破 Oracle 保持 9 年的纪录，国产库首次登顶 |
| 2020 | TPC-C **7.07 亿 tpmC** + 独立成立公司 | 超 Oracle 23 倍；正式商业化独立运作 |
| 2021 | **3.0 HTAP** + 6 月全面开源 | TPC-H 1526 万 QphH@30000GB 登顶，全球唯一同时登顶 TPC-C/TPC-H 的分布式库；开放 300 万行核心代码 |
| 2022 | **4.0** | 单机分布式一体化 + 公有云发布 |

- 来源：[OceanBase 官方发展历程](https://www.oceanbase.com/docs/common-oceanbase-database-cn-1000000005282607) · [OceanBase 关于我们·里程碑](https://www.oceanbase.com/about)（**一手**）

### GoldenDB（2014—2024）

| 时间 | 事件 |
|---|---|
| 2014 | 中兴与中信银行联合立项，定位金融级交易型分布式数据库 |
| 2015-09 | 中信冠字号查询系统上线（第一个业务） |
| 2016—2017 | 门户网站、金融同业平台、零售统一积分陆续上线；启动总行核心改造验证 |
| 2019-06 | 以 50 项评测全满分通过工信部第八批大数据产品能力测评 |
| 2019-10-26 | 信用卡核心 StarCard 投产——**国内首个在大型银行核心业务系统投产的国产数据库** |
| 2020-05-03 | 总行账务核心投产——**国内首个在大型银行账务核心投产的国产数据库** |
| 2021-03 / 11 | v6.0 发布 / 投资成立金篆信科独立运营 |
| 2022-05 / 08 | 国开行新一代核心上线 / 国泰君安低延时核心交易系统（1500 万客户） |
| 2023-04 | v7.1 发布；同年广发银行分布式银行核心 + 信用卡核心投产 |
| 2024-01 | 建行全行对私核心投产，助其完成主机核心分布式改造 |

- 来源：[GoldenDB 百度百科词条（逐年事件）](https://baike.baidu.com/item/goldendb%E6%95%B0%E6%8D%AE%E5%BA%93/23612342)（二手汇编）· [中兴官网《金融业数据库供应链安全发展报告 2022》](https://www.zte.com.cn/content/zte-site/www-zte-com-cn/china/about/news/20221118c2.html)（一手）

### GaussDB / openGauss（2001—2024）

| 时间 | 事件 |
|---|---|
| 2001—2013 | 华为数据库技术积累：DopraDB（2001 内存库）→ GMDB → 2012 高斯部成立 → Gauss OLAP |
| 2014 / 2015 | Gauss OLAP 首个产品版本，进入工行总行 EDW 项目 / 在工行上线 |
| 2018-03 | Gauss OLTP 在招商银行综合支付交易系统投产（日均 8500 万请求、峰值 3500 TPS）；首个 Gauss HATP 落地民生银行 |
| 2019-05-15 | **GaussDB 品牌正式全球发布**；9 月宣布开源 |
| 2020-06-30 | **openGauss 正式面世开源**；7 月发布 GaussDB(for MySQL) 与 NoSQL；8 月并入华为云 |
| 2021 | openGauss 2.0.0；GaussDB Ustore 存储引擎 |
| 2022-04 / 08 | 邮储个人核心基于鲲鹏 + openGauss + GaussDB 投产 / GaussDB 内核获 **CC EAL4+** 安全认证 |
| 2023-06-07 | 华为智慧金融峰会发布**新一代分布式 GaussDB**（全栈自主） |
| 2024-05-06 | GaussDB 基础版发布（面向中小企业） |

- 来源：[华为官网/百科 GaussDB 词条](https://baike.baidu.com/item/gaussdb/63064379) · [凤凰网：华为发布全栈自主 GaussDB](https://news.ifeng.com/c/8QQIrJiZ4VF)（权威媒体）· [GaussDB 发展历程（德邦研究所整理）](https://www.sgpjbg.com/hyshuju/9cec200e5d170afd09fbf6aeabf56b93.html)（二手汇编）

### TiDB（2015—2024）

| 时间 | 事件 |
|---|---|
| 2015-04 / 09 | PingCAP 成立 / TiDB GitHub 开源（一月 Star 超 2700） |
| 2016-08 | A 轮融资；**第一家客户生产环境使用** |
| 2017-06 | B 轮 1500 万美元；TiKV 演进 |
| 2018 | 北京银行生产部署（两地三中心五副本）；TiKV 进入 CNCF Sandbox；C 轮 5000 万美元 |
| 2019-06 / 08 / 09 | 3.0 GA / AskTUG 社区上线 / TiKV 晋级 CNCF 孵化 |
| 2020-05 | **4.0 GA**（支持大事务、RC 隔离、悲观锁——金融核心关键特性） |

- 来源：[PingCAP 发展历程](https://idiks.com/about-cn)（厂商官方汇编）· [北京银行案例](https://pingcap.com/case-studies/how-bank-of-beijing-achieves-database-scaling-without-downtime)（一手）

> **共性规律**：2014—2024 十年间，国产库形成稳定范式——**先内部/外围打磨（3—5 年）→ 完整 SQL/Oracle 兼容降低迁移成本 → 首个「天使客户」核心上线 → TPC-C/权威认证背书 → 规模化复制**。选型时优先考察候选库是否走完这条完整链路。

### 实证：微众银行的分场景数据库选型（2014—2021）

微众银行数据库运维负责人的一手编年史，完整呈现了一家从成立起就不走 IOE 集中式路线的银行，如何按业务场景演进数据库架构——**核心逻辑是"没有银弹，不同场景用不同数据库"**：

| 阶段 | 架构背景 | 数据库选型与部署 | 关键取舍 |
|---|---|---|---|
| **2014—2016** 两地三中心 | 同城两生产中心 + 异地灾备；以 DCN（Data Center Node）为单元做单元化，每个 DCN 是一套从应用到数据库自包含的逻辑单位，按客户号 hash 分片、容量满即扩容 | TDSQL：MySQL 内核定制（主备强一致、性能损失小）、全兼容 MySQL 协议（迁移难度低）、已在腾讯计费场景验证。同城主 SET（一主二备）+ 同城备 SET + 异地备 SET（一主一备） | 2014 年满足金融级的国产分布式库极少；单元化以成本与效率为出发点 |
| **2016—2018** 同城多活 | 两地三中心暴露四问题：同城同步准实时 RPO≠0、仅 DCN 分片粒度多活、人工切换 RTO 约 2 小时、同城 6 副本成本高 | 同城增设第三中心（IDC 2.0），改为单 SET 三副本跨三中心；主节点读写、备节点只读，强一致同步 + 秒级自动切换 | 代价是跨中心流量（应用→主节点、主备同步），靠机房距离 20—50km、专线多路径、万兆改造把网络延迟控制在 2ms 内。结果：同城 RPO=0、RTO 秒级，副本从 6 降到 3 |
| **2018—2020** 引入 NewSQL | DCN 数量激增，非 DCN 的中后台（安全存证等）单实例 TDSQL/MySQL 遇 3TB 容量上限；传统分库分表对开发与 DBA 均不友好 | 选 TiDB：Share-Nothing 存算分离、水平扩展对业务透明、MySQL 协议兼容、开源活跃。先在边缘业务灰度，准实时同步一份到 TDSQL 兜底，再逐步扩展到安全、监控、归档、反欺诈、反洗钱、历史明细查询 | 存证类数据只增不删，单实例不能超 3TB（SSD 单盘 + 运维复杂性限制）；宁可吃螃蟹也不走分库分表老路 |
| **2020—2021** 核心批量 | 贷款核心日终批量与联机复用 DCN 内 TDSQL：耗时近 3 小时、批量高负载冲击联机、受 MySQL 复制原理限制无法靠加并发提速 | TDSQL 近实时同步数据到 TiDB 集群做汇总，批量应用在 TiDB 上计算加工；与联机资源完全解耦 | 目标：微粒贷批量压到半小时内 + 数据库可水平伸缩。经过约一年优化与灰度达标 |

从这套演进中提炼出的工程要点：

- **SQL 模型先重构**：批量 SQL 做 batch 化、热点静态数据加缓存、复杂 SQL 优化内存与执行计划——换库之前先把应用侧优化做尽。
- **新库上线要兜底**：TiDB 初期准实时同步一份数据到 TDSQL，边缘业务灰度验证稳定后再扩面；新产品"成熟一个、替代一个"。
- **热点打散需厂商协同**：Share-Nothing 架构下超大表（数亿级）导入易形成单分片热点，微众联合厂商开发表预打散功能规避。
- **跨库同步做三层校验**：同步工具高可用（无单点、故障自恢复）+ 全方位监控（状态/延迟/两端存活）+ 应用层按分片算 CRC 并比对、再做条目数最终一致性校验。
- **批量要有重跑兜底**：断点续跑预案 + 定期生产演练；批前 rename 备份表支持快速重跑；冷备数据支持极端灾难下重建库重跑。

> **选型启示**：TDSQL 继续承载 DCN 核心系统，TiDB 补充非 DCN 架构下对容量和扩展性要求高的中后台与批量场景。选型不是选"最强"的库，而是为每个场景选**最合适**的库——这正是"数据库没有银弹"的落地含义。

来源：[微众银行数据库架构编年史](https://mp.weixin.qq.com/s?__biz=MzIxMjI0NjQwNQ==&mid=2654192653&idx=1&sn=60051e1ec50f6f76b947dfea66265a0e)（微信公众号 TCTP，2021-10，作者为微众银行数据库运维负责人 enochhu，一手）。

### AI 原生能力

2026 年各家的竞争重心已从「TPC-C 刷榜」转向 **AI 原生 + 湖库一体 / 多模**：OceanBase 4.4.2 LTS（TP/AP/AI 一体）、TDSQL TDAI、PolarDB-X AI Function + 向量索引、达梦 DM9 原生向量、GoldenDB 向量版、openGauss 向量检索 +40%。选型时应把「向量/多模/Agent 记忆」纳入评估项，而不仅是 OLTP 吞吐。

## 国际参考

| 产品 | 背景 | 说明 | 链接 |
|---|---|---|---|
| CockroachDB | 美国 | 分布式 SQL，兼容 PostgreSQL；SIGMOD 2020 系统论文 | [GitHub](https://github.com/cockroachdb/cockroach) |
| YugabyteDB | 美国 | 开源分布式 SQL，设计源自 Spanner | [GitHub](https://github.com/yugabyte/yugabyte-db) |
| Spanner | Google | 全球分布式数据库鼻祖（TrueTime） | [论文](https://research.google/pubs/spanner-googles-globally-distributed-database/) |
| AWS Aurora | 亚马逊 | 计算存储分离（准分布式） | [产品页](https://aws.amazon.com/rds/aurora/) |
| Vitess | 开源 | MySQL 分库分表中间件（YouTube / Slack 在用） | [GitHub](https://github.com/vitessio/vitess) |
| FoundationDB | Apple | 解耦架构分布式 KV，严格可串行化 + 确定性仿真测试 | [GitHub](https://github.com/apple/foundationdb) |

## 选型关注点

- **一致性协议**：多数派共识（Raft / Paxos）保证 RPO=0
- **语法兼容**：MySQL / Oracle 兼容度决定迁移改造成本
- **分布式事务**：全局一致性（TSO / HLC）跨库事务能力；2PC / XA / TCC 支持
- **金融资质**：是否通过银行核心级验证（**稳定运行年限**比「某系统上线」更有说服力，如 GoldenDB 中信 6 年+）
- **容灾能力**：同城双活 / 两地三中心 / 三地五中心部署形态支持
- **生态工具**：数据迁移、校验、回滚工具链是否完备（如 TDSQL 的 DTS-DBbridge、OceanBase 的 OMS）
- **AI 原生**：向量检索、多模数据、库内 AI 推理能力

## 实操验证建议

选型不能只看材料，建议按以下步骤亲手验证：

| 步骤 | 动作 | 验证什么 |
|---|---|---|
| **搭环境** | Docker 跑 OceanBase 社区版或 TiDB，配多副本 | 观察副本角色、故障切换时的主副本迁移 |
| **压分片键** | 按目标业务的真实分片键建表并压测 | 携带/不携带分片键的 TPS 差异、跨分片事务占比——这是银行核心迁移的关键指标 |
| **注入故障** | kill 主副本、断网，观察 RTO 与数据一致性 | 验证厂商宣称的 RPO=0 是否属实（方法见 [docs/migration.md](docs/migration.md)） |
| **测兼容** | 用迁移工具扫描存量 Oracle/MySQL 的存储过程、触发器、语法差异 | 提前量化改造工作量，避免投产前突击 |
| **查资质** | 核对候选库是否有同规模银行核心的长期稳定运行记录 | 「上线过」≠「跑稳过」，运行年限比单一上线案例更有说服力 |

> 认证课程（OceanBase OBCA/OBCP、TiDB PCTA/PCTP、GaussDB HCIA/HCIP）适合系统性入门，但替代不了针对自身业务场景的压测与故障验证。
