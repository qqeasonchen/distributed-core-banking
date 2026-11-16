# 论文、白皮书与标准

> 条目格式："标题 + 来源 + 年份 + 链接 + 一句话摘要"。

## 学术论文

| 论文 | 出处 | 摘要 |
|---|---|---|
| [OceanBase: A 707 Million tpmC Distributed Relational Database System](https://www.vldb.org/pvldb/vol15/p3385-xu.pdf) | PVLDB 15(12), VLDB 2022 | OceanBase 官方技术论文：Shared-nothing 原生分布式架构、Paxos 多数派（RPO=0, RTO<30s）、LSM-Tree 存储引擎、7.07 亿 tpmC TPC-C 细节 |
| [Spanner: Google's Globally-Distributed Database](https://research.google/pubs/spanner-googles-globally-distributed-database/) | OSDI 2012 | 全球分布式数据库奠基之作，TrueTime 全局时钟 + 跨洲强一致 |
| [F1: A Distributed SQL Database That Scales](https://research.google/pubs/f1-a-distributed-sql-database-that-scales/) | VLDB 2013 | 基于 Spanner 的分布式 SQL 数据库 |
| [In Search of an Understandable Consensus Algorithm (Raft)](https://raft.github.io/raft.pdf) | USENIX ATC 2014 | Raft 共识算法原论文，多数分布式数据库副本一致性的基础 |
| [The Tail at Scale](https://research.google/pubs/the-tail-at-scale/) | CACM 2013 | 大规模分布式系统长尾延迟治理，金融核心性能设计必读 |

## 白皮书 / 报告

- 中国信通院（CAICT）：《分布式数据库金融应用》《金融分布式架构》系列研究报告 —— ccid 相关发布页可检索
- 金融信创生态实验室：金融信创解决方案目录与试点名单
- 厂商白皮书：
  - 蚂蚁《金融机构分布式架构白皮书》
  - 腾讯云《金融分布式数据库 TDSQL 白皮书》
  - 华为《金融核心现代化》系列
  - 中兴通讯 GoldenDB 金融级分布式数据库白皮书
- IDC / Gartner：Core Banking Platforms 厂商评估（MarketScape / Magic Quadrant）

## 行业标准 / 监管文件

- 人民银行金融行业标准：如《金融分布式账本技术安全规范》（JR/T 0192）
- 原银保监会：银行业信息科技风险管理指引、外包与自主可控相关文件
- 金融行业信创适配目录（金融信创生态实验室发布）

## 会议 / 期刊

- 《金融电子化》杂志：银行业信息化官方期刊，核心改造案例主阵地
- 技术大会：QCon / ArchSummit 金融科技专场、OceanBase DevCon、TiDB DevCon、DTCC（中国数据库技术大会）

## 延伸阅读建议

1. 先读 **Spanner 论文**建立"分布式数据库为什么能强一致"的直觉
2. 再读 **OceanBase VLDB 2022** 看工业界如何落地到金融核心场景
3. 对照 **Raft 论文**理解 Multi-Raft 的工程细节
