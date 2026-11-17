# Distributed Core Banking / 金融分布式核心银行系统资料集

收集整理分布式核心银行系统（Distributed Core Banking System）的相关资料：概念、架构、迁移工程、分布式数据库、中间件、基础设施与运维应急、厂商方案、银行实践案例、标准论文与学习资源。按"资料层 / 知识层"两层组织，详见下方目录。

> 中文语境下"分布式核心"指将传统集中式（大型机 + 集中式数据库）的核心银行系统改造为微服务 + 分布式数据库架构的新一代核心系统，兼有国产化替代（信创）的时代背景。

## 目录

| 文件 | 内容 |
|---|---|
| [timeline.md](timeline.md) | **发展时间线（2014—2026）**：政策、产品、案例、国际脉络四条线 |
| [databases.md](databases.md) | 分布式数据库：OceanBase、TDSQL、GaussDB、GoldenDB 等 |
| [middleware.md](middleware.md) | **中间件**：消息总线→EventMesh/ServiceMesh 演进、WeRedis 缓存与持久化 KV 选型（微众银行一手实践） |
| [vendors.md](vendors.md) | 厂商与产品：国际（Temenos、Fiserv）与国内（长亮、宇信等） |
| [cases.md](cases.md) | 银行实践案例：大行去主机收官、省级农信、国际案例 |
| [infrastructure.md](infrastructure.md) | **基础设施**：数据中心机房、全三层网络搬迁、POD 迁移与裁撤、WeCloud 运维风控、蓝光存储归档（微众银行一手实践） |
| [ecc.md](ecc.md) | **运维应急**：UIOC 故障处置升级流程、角色固化与清单化、三级升级、告警治理（微众银行一手实践） |
| [papers.md](papers.md) | 论文、白皮书与行业标准（含 JR/T 0203/0204/0205 精确标准号） |
| [resources.md](resources.md) | 学习资源：课程、博客、开源项目、迁移工程方法 |
| [concepts.md](concepts.md) | **概念层**：Core Banking、业务模块全景、复式记账、客户与账户体系、工程判断与常见误区 |
| [architecture.md](architecture.md) | **方案层**：从业界案例提炼——单元化、多活容灾、分片键、流量切换、热点账户、业会分离、双余额日切、产品工厂 |
| [migration.md](migration.md) | **工程层**：渐进式替换、CDC、一致性校验、分布式事务、对抗性验证、灰度切换 |

资料按两层组织：`concepts.md` / `architecture.md` / `migration.md` 三份文档为**知识层**，从业界主流真实实践提炼可复用的方案、判据与踩坑经验；其余文档为**资料层**（时间线、案例、数据库、中间件、基础设施、运维应急、厂商、标准论文、学习资源）。两层互不复述、交叉索引——案例档案在资料层，方法与知识点在概念/方案/工程三份文档。

## 来源标注约定

`一手` = 银行/厂商官网、年报、官方署名文章；`二手` = 权威媒体或第三方转述；`待核实` = 仅搜索摘要命中。数字以原文为准，二手来源不建议直接当结论引用。

## 核心概念速览

**Core Banking**：银行支撑基础业务运转的后台核心系统（客户账户、存款、贷款、支付结算、总账会计）。

**金融分布式核心**：= Core Banking + 分布式技术架构。业务职能不变，架构从"大型机集中式"变为"x86 集群 + 微服务 + 分布式数据库"。

## 贡献

欢迎提交 Issue / PR 补充资料。提交时请注明资料来源与大致分类。

## License

[CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)
