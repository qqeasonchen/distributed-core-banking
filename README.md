# Distributed Core Banking / 金融分布式核心银行系统资料集

收集整理分布式核心银行系统（Distributed Core Banking System）的相关资料：概念、架构、分布式数据库、厂商方案、银行实践案例与学习资源。

> 中文语境下"分布式核心"指将传统集中式（大型机 + 集中式数据库）的核心银行系统改造为微服务 + 分布式数据库架构的新一代核心系统，兼有国产化替代（信创）的时代背景。

## 为什么做这个项目

- 核心银行系统（Core Banking）是银行的后台核心：账户、存贷、支付、总账，宕机即全行停摆
- 国内大型银行正在经历 "去 IOE" / 信创驱动的核心系统分布式化改造浪潮
- 相关资料分散在各厂商白皮书、银行公众号、论文中，缺乏系统整理

## 目录

| 文件 | 内容 |
|---|---|
| [timeline.md](timeline.md) | **发展时间线（2014—2026）**：政策、产品、案例、国际脉络四条线 |
| [databases.md](databases.md) | 分布式数据库：OceanBase、TDSQL、GaussDB、GoldenDB 等 |
| [vendors.md](vendors.md) | 厂商与产品：国际（Temenos、Fiserv）与国内（长亮、宇信等） |
| [cases.md](cases.md) | 银行实践案例：大行去主机收官、省级农信、国际案例 |
| [papers.md](papers.md) | 论文、白皮书与行业标准（含 JR/T 0203/0204/0205 精确标准号） |
| [resources.md](resources.md) | 学习资源：课程、博客、开源项目、迁移工程方法 |
| [docs/business-modules.md](docs/business-modules.md) | **业务层**：核心系统业务模块、技术痛点与解决方案（热点账户、业会分离、日切、产品工厂等） |
| [docs/concepts.md](docs/concepts.md) | **概念层**：Core Banking、复式记账、分布式核心的分层、工程判断与常见误区 |
| [docs/architecture.md](docs/architecture.md) | **方案层**：从业界案例提炼——单元化、多活容灾、分片键、流量切换 |
| [docs/migration.md](docs/migration.md) | **工程层**：绞杀者模式、CDC、一致性校验、对抗性验证、灰度切换 |

资料按两层组织：`docs/` 四份文档为**知识层**，从业界主流真实实践提炼可复用的方案、判据与踩坑经验；根目录文档为**资料层**（具体案例、产品、时间线、政策）。两层互不复述、交叉索引——案例档案在根目录，方法与知识点在 `docs/`。

## 来源标注约定

`一手` = 银行/厂商官网、年报、官方署名文章；`二手` = 权威媒体或第三方转述；`待核实` = 仅搜索摘要命中。数字以原文为准，二手来源不建议直接当结论引用。

## 核心概念速览

**Core Banking**：银行支撑基础业务运转的后台核心系统（客户账户、存款、贷款、支付结算、总账会计）。

**金融分布式核心**：= Core Banking + 分布式技术架构。业务职能不变，架构从"大型机集中式"变为"x86 集群 + 微服务 + 分布式数据库"。

英文表述：**Distributed Core Banking System**（标准）、Cloud-Native Core Banking（云原生语境）、Core Banking Transformation（改造工程语境）。

## 贡献

欢迎提交 Issue / PR 补充资料。提交时请注明资料来源与大致分类。

## License

[CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)
