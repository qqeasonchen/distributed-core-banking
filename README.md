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
| [docs/concepts.md](docs/concepts.md) | 核心概念：Core Banking、集中式 vs 分布式、信创 |
| [docs/architecture.md](docs/architecture.md) | 架构方案：微服务、分布式数据库、事务一致性、异地多活 |
| [docs/migration.md](docs/migration.md) | 迁移方法论：双轨并行、灰度切流、数据核对 |
| [databases.md](databases.md) | 分布式数据库：OceanBase、TDSQL、GaussDB、GoldenDB 等 |
| [vendors.md](vendors.md) | 厂商与产品：国际（Temenos、Fiserv）与国内（长亮、宇信等） |
| [cases.md](cases.md) | 银行实践案例：大行去主机收官、省级农信、国际案例 |
| [papers.md](papers.md) | 论文、白皮书与行业标准（含 JR/T 0203/0204/0205 精确标准号） |
| [resources.md](resources.md) | 学习资源：课程、博客、开源项目、迁移工程方法 |

## 2026-11 更新摘要

本轮全网检索补充的主要内容（各文件内以 🔄 标记）：

1. **案例**：2025 年是国有大行「去主机」收官年——工行 2025-11-07 最后一台主机关停、农行 2025-04 最大规模主机下线、建行境内外全部核心下移、中行史上最大批次投产；新增省级农信（四川/贵州/广西）与政策性银行（国开行/农发行）案例；新增国际案例（Thought Machine / Temenos / Finacle / 英格兰银行 RT2）
2. **论文与标准**：补 12 篇经典论文（Paxos 系列、Percolator、Calvin、CockroachDB 等）、6 篇 2024—2026 新论文（TDSQL / GaussDB PVLDB 2024 等）、JR/T 0203/0204/0205 等 8 项精确标准
3. **数据库**：补 OceanBase / TDSQL / GaussDB / GoldenDB / PolarDB / 达梦 / 金仓 2025—2026 进展，新增「AI 原生能力」评估维度
4. **厂商**：补 Oracle / Finastra / TCS BaNCS / Backbase 等 8 家国际厂商与科蓝/南天/润和/京北方等国内厂商，新增市场格局与经营健康度分化
5. **工程方法**：工行六步实施工艺、交易回放两层级比对、混沌演练、流批一体 + 事件驱动持续对账

> **来源标注约定**：`一手` = 银行/厂商官网、年报、官方署名文章；`二手` = 权威媒体或第三方转述；`待核实` = 仅搜索摘要命中。关键数字已逐项核对原文，二手来源不建议直接当结论引用。

## 核心概念速览

**Core Banking**：银行支撑基础业务运转的后台核心系统（客户账户、存款、贷款、支付结算、总账会计）。

**金融分布式核心**：= Core Banking + 分布式技术架构。业务职能不变，架构从"大型机集中式"变为"x86 集群 + 微服务 + 分布式数据库"。

英文表述：**Distributed Core Banking System**（标准）、Cloud-Native Core Banking（云原生语境）、Core Banking Transformation（改造工程语境）。

## 贡献

欢迎提交 Issue / PR 补充资料。提交时请注明资料来源与大致分类。

## License

[CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)
