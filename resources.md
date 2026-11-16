# 学习资源

## 开源项目

### 基础项目

| 项目 | 说明 | 链接 |
|---|---|---|
| OceanBase | 蚂蚁原生分布式数据库 | [GitHub](https://github.com/oceanbase/oceanbase) · [社区](https://www.oceanbase.com/community) |
| TiDB | PingCAP 分布式 HTAP 数据库 | [GitHub](https://github.com/pingcap/tidb) · [AskTUG 社区](https://asktug.com) |
| openGauss | 华为开源数据库 | [Gitee](https://gitee.com/opengauss) · [官网](https://opengauss.org/zh/) |
| Seata | 阿里分布式事务框架（v2.6.0，2026-01；AT/TCC/SAGA/XA 四模式） | [GitHub](https://github.com/apache/incubator-seata) · [官网](https://seata.io/) |
| SOFAStack | 蚂蚁金融分布式中间件全家桶 | [GitHub](https://github.com/sofastack) · [官网](https://www.sofastack.tech) |
| WeCube / WeBankPartners | 微众银行开源运维与区块链生态 | [GitHub](https://github.com/WeBankPartners) |
| ShardingSphere | 分布式数据库中间件生态（JDBC / Proxy / Sidecar 三种形态） | [GitHub](https://github.com/apache/shardingsphere) |
| CockroachDB / YugabyteDB | 国际分布式 SQL 参考 | [crdb](https://github.com/cockroachdb/cockroach) · [yugabyte](https://github.com/yugabyte/yugabyte-db) |

### 金融核心中间件

| 项目 | 说明 | 链接 |
|---|---|---|
| **Apache EventMesh** | CloudEvents 原生事件网格，诞生于微众银行、首个进入 ASF 的中国金融项目，2023 毕业为 TLP；支持 A2A 协议与 OpenTelemetry 原生追踪 | [官网](https://eventmesh.apache.org/zh/) · [GitHub](https://github.com/apache/eventmesh) |
| **Apache RocketMQ** | 事务消息/顺序消息，金融支付异步化与最终一致的常用底座 | [官网](https://rocketmq.apache.org/) |
| **Apache Kafka** | 高吞吐事件日志，Flink 对账/批流一体的事实标准数据源 | [官网](https://kafka.apache.org/) |
| **Apache Dubbo / Nacos / Sentinel** | RPC、服务发现+配置、流量控制与熔断降级（金融核心服务化常用组合） | [Dubbo](https://github.com/apache/dubbo) · [Nacos](https://nacos.io/) · [Sentinel](https://sentinelguard.io/) |
| **Mycat2** | 兼容 MySQL 协议的分布式数据库中间件 | [GitHub](https://github.com/MyCATApache/Mycat2) |
| **Apache Doris / StarRocks** | 实时 OLAP，金融实时报表与对账；VBill 支付案例用 StarRocks 替代 Hive+Kudu+HBase，批处理扫描量 -73% | [Doris](https://doris.apache.org/) · [StarRocks 案例](https://www.starrocks.io/blog/vbill-payment-handling-billions-of-records-in-real-time-with-starrocks) |
| **Apache Flink** | 流批统一引擎；AWS × Zeta 案例用 Flink+Kafka 实现 **2.08 亿信用账户 40 分钟完成 EOD** | [官网](https://flink.apache.org/) · [AWS 案例](https://aws.amazon.com/solutions/case-studies/zeta-amazon-eks/) |
| **Canal** | MySQL binlog 订阅/CDC，数据迁移与准实时对账的关键组件 | [GitHub](https://github.com/alibaba/canal) |

### 银行核心开源实现与可观测性

| 项目 | 说明 | 链接 |
|---|---|---|
| **Apache Fineract** | 云就绪核心银行平台，headless + Open API；面向普惠/未银行人群，**Fineract-CN 微服务版已于 2023-05 归档**；适合架构学习与 API 设计参考，不等同于大额支付核心生产实现 | [官网](http://fineract.apache.org/) · [GitHub](https://github.com/apache/fineract) |
| **Mifos X** | 基于 Fineract 的 Web/移动端参考分发版，400+ 机构、2000 万+ 客户 | [mifos.org](https://mifos.org/) |
| **OpenBankProject** | 开放银行 API 平台，支持 XS2A/PSD2/Open Finance，AGPL-3.0 | [GitHub](https://github.com/OpenBankProject) |
| **Apache SkyWalking** | 国产 APM，微服务/云原生全栈可观测，原生接入 OTLP | [官网](https://skywalking.apache.org/) |
| **OpenTelemetry / Prometheus** | 云原生遥测事实标准与时序监控标配 | [OTel](https://opentelemetry.io/) · [Prometheus](https://prometheus.io/) |
| **AppActive**（阿里） | 多活容灾中间件，提供多活标准、实现与 Demo，覆盖单 AZ→多地域→多云；**核心代码停留在 2021—2022，低活跃维护** | [GitHub](https://github.com/alibaba/Appactive) · [文档](https://doc.appactive.io/) |

### 金融开源项目起源时间线（2014—2024）

> 选型时「项目活了多久」和「还在不在活跃维护」同样重要。以下标注诞生/毕业时间，⚠️ 标注低活跃项目。

| 时间 | 项目 | 起源/里程碑 |
|---|---|---|
| 2015-09 | **TiDB** | PingCAP 开源，一月 Star 超 2700；2018 TiKV 入 CNCF、2020 4.0 GA |
| 2016 | **Apache EventMesh 前身** | 诞生于微众银行；2021 捐给 Apache，2023-05 毕业成为 ASF 顶级项目（TLP），**首个进入 ASF 的中国金融项目** |
| 2017 | **Seata** | 阿里开源分布式事务框架（原 Fescar），2019 进入 Apache 孵化器 |
| 2017-04 | **FISCO BCOS** | 微众银行等金链盟成员孵化的国产金融联盟链底层平台，2019 开源 |
| 2018-08 | **TiKV / TiDB Operator** | 进入 CNCF Sandbox |
| 2019-08 | **AskTUG** | TiDB 中文社区论坛上线 |
| 2020-06-30 | **openGauss** | 华为开源关系型数据库 |
| 2020-07 | **Chaos Mesh** | PingCAP 开源云原生混沌工程平台，进入 CNCF 沙箱 |
| 2021-06-01 | **OceanBase 社区版** | 从 3.1.0 起开放源码 |
| 2021 | **AppActive** | 阿里多活容灾中间件开源 ⚠️ 核心代码停留在 2021—2022，低活跃维护 |
| 2023-05 | **Apache Fineract-CN** | 微服务版归档 ⚠️ 仅保留参考学习价值 |

> **判断**：金融中间件开源有两条清晰脉络——**2015—2017 数据库/事务层**（TiDB、Seata、OceanBase），**2020 后云原生/可观测/混沌层**（Chaos Mesh、OpenTelemetry、EventMesh TLP）。老项目要核查维护活跃度，归档/低活跃项目（Fineract-CN、AppActive）只作架构学习，不进生产选型。

## 学习路径建议

1. **入门**：理解 Core Banking 功能范围（[docs/concepts.md](docs/concepts.md)）
2. **数据库**：读一篇 OceanBase 或 TiDB 架构文章，理解 Multi-Raft / 数据分片 / 分布式事务
3. **中间件**：了解 SOFAStack、Seata、EventMesh 的金融分布式实践
4. **案例**：读张家港农商行（首例）、工商银行（2025 主机全面关停）、邮储银行（六大行代表）、四川农商（省级农信首例）的公开披露（见 [cases.md](cases.md)）
5. **深度**：跟踪《金融电子化》与信通院报告（见 [papers.md](papers.md)）

## 社区

- [OceanBase 社区](https://www.oceanbase.com/community)：技术文章、课程与认证
- [TiDB 社区](https://asktug.com)：AskTUG 中文问答社区
- [dbaplus 社群](https://www.dbaplus.cn)：企业级 Data/AIOps 社群，14 万+ 订阅号
- [墨天轮](https://www.modb.pro/)：中国数据库流行榜、国产库实操与信创案例
- 金融信创生态实验室、北京金融科技产业联盟：金融信创适配与试点活动
- [InfoQ 中国](https://www.infoq.cn)：金融架构专题
- 公众号「老纪的技术唠嗑局」（OceanBase 开源负责人）：特性原理与运维实践，[社区推荐帖](https://ask.oceanbase.com/t/topic/35619712/7)

## 认证与课程

- OceanBase 官方认证：[OBCA / OBCP](https://www.oceanbase.com/training)；[OceanBase 基础课（免费公开课）](https://time.geekbang.org/opencourse/intro/100115401)
- TiDB 认证：PCTA / PCTP（PingCAP 官网）
- GaussDB 认证：华为 HCIA / HCIP Database
- 极客时间[《分布式数据库 30 讲》](https://time.geekbang.org/column/intro/100057401)：讲师王磊（光大银行首席数据架构师），金融视角强
- 电科金仓 KCA/KCP/KCM 认证体系

## 推荐书单（中文）

- 《数据密集型应用系统设计》（DDIA）—— 分布式数据系统通识经典
- 《金融数据库转型实战：基于 OceanBase》（2025-01，电子工业出版社，太保科技数智研究院著，ISBN 9787121494741）—— 10 章涵盖选型标准、配置基线、核心攻坚、迁移案例、备份恢复
- 《分布式数据库系统原理》（各数据库官方文档是最好的教材）
- OceanBase / TiDB 官方博客的架构系列文章

## 架构专题资料

| 主题 | 资料 | 说明 |
|---|---|---|
| 单元化 / LDC | [AppActive 官方文档](https://github.com/alibaba/Appactive/tree/main/docs/cn) · [《应用多活技术白皮书》（阿里云，2022）](https://www.alibabacloud.com/blog/599067) | 多活标准 + 实现 + Demo 的工程化参照 |
| 分布式事务 | [Seata 官网](https://seata.io/) · [《Seata 与分布式事务的本质解析》（2025-09）](https://kingson4wu.github.io/zh/posts/20250917-seata/) | 四模式对比；**资金类业务必须走 TCC/SAGA 在业务层冻结+补偿**，AT 仅限可控内部 CRUD |
| 日终批处理改造 | [AWS × Zeta EOD 案例](https://aws.amazon.com/solutions/case-studies/zeta-amazon-eks/) · [VBill × StarRocks](https://www.starrocks.io/blog/vbill-payment-handling-billions-of-records-in-real-time-with-starrocks) | 流批一体 + 事件驱动持续对账替代 T+1 批量对账 |
| 核心系统上云 | [腾讯云《商业银行核心系统分布式转型白皮书》（2025-07）](https://www.cet.com.cn/wzsy/kjzx/10234306.shtml) · [华为分布式新核心解决方案 5.5](https://support.huawei.cn/cn/blogs/2025/industries/finance/finance-core) | 多地多活 + 单元化；某股份制银行 RPO=0、RTO<60 秒 |
| HTAP / Serverless | [TiDB Serverless 与 TiFlash](https://cloud.baidu.com/article/5039420) · 金仓 Serverless+HTAP | 实时风控场景下 OLTP/OLAP 互不干扰 |

## 迁移工程方法体系

| 环节 | 资料 | 要点 |
|---|---|---|
| **交易回放比对** | [农行研发中心《分布式核心银行系统的测试研究与实践》（《金融电子化》2020-05）](http://mp.weixin.qq.com/s?__biz=MjM5MzA3MzAzOQ==&mid=2655478962&idx=3&sn=ec2e54f14782262d8400c2433d2b3ec0) · 神州信息 Sm@rtComplay · 华青融天 EZSonar | 生产日志脱敏回放；网络流量录制 + 旁路 TAP 镜像；**交易级 + 数据库级两层级比对** |
| **数据核对平台** | [Wallet Reconciliation（2026-08）](https://www.besthub.dev/articles/how-to-secure-wallet-funds-at-billion-scale-through-reconciliation-balance-checks-channel-matching-and-auto-repair-80148a0bdc29) · StarRocks 对账 3.0 | 采集/标准化/核对/差异中心/修复/治理六层架构；Flink SQL 分钟级差异检测 |
| **混沌工程** | [ChaosBlade](https://chaosblade.io/) · 中电金信银行核心测试方案 | 网络延迟/服务宕机/CPU 抢占故障注入，爆炸半径与自动中止安全控制 |
| **全链路压测** | 农行分布式核心性能测试实践（同上农行链接） · [dbaplus](https://www.dbaplus.cn) | JMeter 单交易基准/负载/混合/稳定场景；类网关统一发压；80% 交易量在 20% 时间内完成推算 TPS |
| **信创适配测试** | [twt：信创数据库核心迁移性能瓶颈应对](https://www.talkwithtrend.com/Question/475851) · 《信创选型实战指南》 | 「主动施压、全链路透视、分层治理」；分片键前置设计；基准性能画像 + APM；脱敏回放 + 混沌演练 |

> **判断**：单靠功能测试用例不足以覆盖分布式核心切换风险；应把**交易回放比对、数据一致性核对、混沌演练、全链路压测**作为一套完整方法体系写入迁移方案（见 [docs/migration.md](docs/migration.md)）。
