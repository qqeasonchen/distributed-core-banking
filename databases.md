# 分布式数据库

金融核心系统分布式化的数据底座。

## 国内主要产品

| 产品 | 背景 | 特点 | 银行案例 | 官方资源 |
|---|---|---|---|---|
| **OceanBase** | 蚂蚁集团 | 原生分布式，TPC-C 7.07 亿 tpmC 世界纪录，兼容 MySQL/Oracle，Paxos 多数派（RPO=0, RTO<30s） | 网商银行、多家股份行 | [文档中心](https://docs.oceanbase.com/zh) · [GitHub](https://github.com/oceanbase/oceanbase) |
| **TDSQL** | 腾讯云 | Shared-Nothing，强同步复制 RPO=0，TPC-C 8.14 亿 tpmC，Oracle 兼容度 95%-98%，2PC/XA 分布式事务 | 邮储银行新核心、张家港农商行、微众银行 | [产品页](https://cloud.tencent.com/product/tddbms) · [金融云开发指南](https://doc.fincloud.tencent.com/document/product/388315/7714) |
| **GaussDB** | 华为 | 分布式 + 集中式双形态，兼容 Oracle | 工行、平安银行、多家股份行 | [华为云 GaussDB](https://www.huaweicloud.com/product/gaussdb.html) |
| **GoldenDB** | 中兴 | 面向金融交易型场景，业界首个分布式事务强一致，具备替换大/小型机能力 | 中信银行（信用卡核心 + 账务核心）、建行对私核心、国开行、广发银行 | [GoldenDB 官网](https://www.ztedb.com) |
| **TiDB** | PingCAP | 开源，HTAP，兼容 MySQL，Multi-Raft | 多家城商行、支付机构 | [文档](https://docs.pingcap.com/zh) · [GitHub](https://github.com/pingcap/tidb) |
| **SequoiaDB（巨杉）** | 巨杉 | 分布式老牌 | 部分银行历史数据层 | [官网](https://www.sequoiadb.com) |
| **openGauss** | 华为开源 | 集中式为主，配套分布式方案 | 信创场景广泛 | [官网](https://opengauss.org/zh/) · [Gitee](https://gitee.com/opengauss) |

### 产品速记

- **OceanBase**：支付宝 100% 核心链路在跑；"三地五中心"城市级故障无损容灾；单机分布式一体化架构（4.x 起）
- **TDSQL**：服务中国 TOP10 银行比例约 70%；配套迁移工具 DTS-DBbridge（Oracle/DB2 → TDSQL）；智能 DBA 工具 DBbrain
- **GoldenDB**：银行基因最深——与中信银行 2014 年联合立项、5 年研发，首个在大型银行账务核心投产的国产数据库（2020）

## 国际参考

| 产品 | 背景 | 说明 | 链接 |
|---|---|---|---|
| CockroachDB | 美国 | 分布式 SQL，兼容 PostgreSQL | [GitHub](https://github.com/cockroachdb/cockroach) |
| YugabyteDB | 美国 | 开源分布式 SQL | [GitHub](https://github.com/yugabyte/yugabyte-db) |
| Spanner | Google | 全球分布式数据库鼻祖（TrueTime） | [论文](https://research.google/pubs/spanner-googles-globally-distributed-database/) |
| AWS Aurora | 亚马逊 | 计算存储分离（准分布式） | [产品页](https://aws.amazon.com/rds/aurora/) |
| Vitess | 开源 | MySQL 分库分表中间件（YouTube / Slack 在用） | [GitHub](https://github.com/vitessio/vitess) |

## 选型关注点

- **一致性协议**：多数派共识（Raft / Paxos）保证 RPO=0
- **语法兼容**：MySQL / Oracle 兼容度决定迁移改造成本
- **分布式事务**：全局一致性（TSO / HLC）跨库事务能力；2PC / XA / TCC 支持
- **金融资质**：是否通过银行核心级验证（长时间稳定运行案例）
- **容灾能力**：同城双活 / 两地三中心 / 三地五中心部署形态支持
- **生态工具**：数据迁移、校验、回滚工具链是否完备（如 TDSQL 的 DTS-DBbridge、OceanBase 的 OMS）

## 学习路径

1. 本地用 Docker 跑一个 OceanBase 社区版或 TiDB，体验多副本与分布式事务
2. 读《OceanBase 系统架构》官方文档，对照 [VLDB 2022 论文](https://www.vldb.org/pvldb/vol15/p3385-xu.pdf)
3. 关注各厂商认证课程（OceanBase 认证、TiDB PCTA/PCTP、GaussDB 认证）
