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

## 工程工具与职业成长

> 开源项目解决"用什么"，这一组解决"怎么构建"与"怎么入门成长"——工程工具（Maven）、学习路径与职业困惑，作为学习资源的补充。

### Maven 入门：坐标 / 依赖 / 仓库 / 生命周期 / 插件

> 实操篇：[其实很多人，对Maven理解的并不深（2020-01-14）](https://mp.weixin.qq.com/s?__biz=MzIzMTk2NjAzMg==&mid=2247484723&idx=1&sn=9c040be9e475b8581a2447f607711b2f)

- Maven 不只是依赖管理工具：把项目开发管理抽象为 POM（pom.xml），跨平台、命令以插件形式集成因此核心很小（几兆）；原理是远程仓库+本地仓库+pom，同一版本 jar 只下载一次，引入 a 会自动带上其依赖 b/c，自动去重与解决冲突，并统一构建过程（银行核心按存款/贷款/公共分模块，每模块一个工程利于分工）。
- 安装配置：检查 JAVA_HOME、解压到非中文无空格路径、配 MAVEN_HOME/Path、mvn -v 验证；IDE 应配自装 Maven 与命令行同版本（避免 jar 下载不全、install 报错）；推荐用户级 ~/.m2/settings.xml 配 localRepository，避免影响其他用户且便于升级；mvn 执行链：PATH 找 mvn→查 settings.xml→本地仓库找插件否则中央仓库下载。
- 坐标五元素：groupId/artifactId/version 必填，packaging 默认 jar，classifier 需配合插件；是构件的"身份证"，使 Maven 能唯一定位并从本地/远程/中央仓库获取构件。
- 依赖：scope 分 compile（随项目发布）、test（如 junit）、provided（如 servlet-api，不随发布）、runtime（JDBC 驱动）、system、import；传递依赖 A→B→C；依赖调节三原则为 optional 不传递、最短路径优先、最先声明优先；exclusions 排除传递依赖（只写 groupId/artifactId 不写 version）。
- 仓库分本地仓库（~/.m2）与远程仓库（中央仓库+私服）；私服（Archiva/Artifactory/Nexus 最流行）缓解外网下载压力、加速构建、作缓存更安全，并便于共享自研或第三方 jar（如短信商 jar）。
- 五大核心概念：坐标、依赖、仓库、生命周期、插件；三套独立生命周期 clean/default/site，调用某阶段会顺序执行其前所有阶段（mvn install 会先编译测试打包）；default 含 validate→compile→test→package→install→deploy 等；生命周期抽象、行为由插件完成（类似模板方法），插件绑定分内置与自定义。

### 银行核心系统学习思路：角色困惑 / 转岗 / 核心系统树 / 成长阶段

> 实操篇：[银行核心系统之学习思路（2018-11-06）](https://mp.weixin.qq.com/s?__biz=MzIzMTk2NjAzMg==&mid=2247484063&idx=1&sn=79cb75da83a7b167ea8b292eccca8b14)

- 银行各角色各有困惑（业务架构嫌需求慢、经理嫌沟通难、实施嫌范围外、维护嫌扩展差、测试嫌乱改代码），"都是围城"需相互理解；名词科普 DM/PM/TM/PL/SA/SE/PG/QA/STE 职责。
- 转岗功课：审视动机（不足一年敢试错，多年者结合趋势避免跳火坑）、定目标规划、关注时事与人行报告而非只看教材、与同行交流、关注银行科技子公司（兴业数金/招银云创/光大科技/建信金科/民生科技）、认清优劣、善用互联网；学好技能是为理解原理、提升沟通而非做码农。
- 把核心系统比作树：树根=技术架构与硬件（JVM/SOA/集中式/分布式，IBM 大机/AS400/X86）、树干=各业务模块（贷款/存款/中间业务/ECIF）、树枝=渠道（网银/ATM/POS/手机银行，高频存取转）、果实=报表系统、树心=ESB 与前置、花朵=监控平台、树皮=柜面。
- 初学阶段：技术从增删改查起步、看日志加 trace、记录并刨根问题；业务上结合功能书看代码，思考为何新增功能、分析字段用途与登记哪些表字段，不懂的术语靠加班百度扫盲。
- 成长阶段：从"怎么做"到"做不做、做多少"，学会砍需求；学银行会计（科目、复式借贷记账、表外、重空管理）、学存款高频交易（定活期开销户/存取/转账/冻结解冻，深挖只收不付/只付不收/预授权及撤销完成/超额冻结/法律冻结/轮候顺序）、学账户体系（大小总账、客户账号与内部户清算、过账迁移总分核对）、学批量（计提结息/假期/靠档计息/全额与超额累进/权责发生制/日终拆分/年终决算）。
- 价值阶段：培养沟通表达、了解支付清算、跳出局部从整体把握应用/数据/技术架构、多分享多交流。

### 开发口头禅（幽默清单，无技术知识点）

> 原文：[开发是不是这样对你说？（2018-03-04）](https://mp.weixin.qq.com/s?__biz=MzIzMTk2NjAzMg==&mid=2247483856&idx=1&sn=396a3650b179dc8f767f6f772f2cbf99)。**如实标注：以幽默清单为主，无技术知识点**，价值在反映测试/业务与开发间的沟通理解问题。

- 盘点开发人员的 26 句经典口头禅（如"明明在我电脑上是可以的"、"快了，已完成 90%"、"只是改一行代码没影响"、"重启下看看"、"这不是 bug 是环境配置问题"、"下班前回你（因为我还没下班）"等），反映测试/业务与开发间的沟通理解问题。
- 提醒业务与测试人员不必委屈，开发也常因时间紧任务重而无助，强调相互理解与尊重以完成项目目标；内容以幽默清单为主，无技术知识点。

## 按角色查阅资源

| 你的任务 | 直接可用的资源 | 用途 |
|---|---|---|
| **理解业务与痛点** | [核心概念与业务模块全景](concepts.md) + [账务模块方案](application.md) | 先看业务模块与账户体系难在哪，再看热点账户、业会分离、日切等解法 |
| **做架构设计** | [单元化与多活方案](architecture.md) + AppActive / Seata / ChaosBlade | 抄可复用方案，关注跨机房调用比例、单元封闭、切流工艺 |
| **做数据库选型** | [数据库能力对比](databases.md) 的选型关注点 + 墨天轮流行榜 | 核对一致性协议、兼容度、金融资质、稳定运行年限 |
| **做迁移方案** | [迁移工程方法](migration.md) + 农行测试实践 + 回放比对工具 | 把回放比对、一致性核对、混沌演练、压测写成完整体系 |
| **做立项/合规** | [标准文号](papers.md) 的 JR/T 0203/0204/0205 + 银监发〔2014〕39 号文 | 立项与验收材料引用依据 |
| **找同业参照** | [银行案例](cases.md)：张家港（首例）、邮储（六大行代表）、四川农商（省级农信首例） | 按同类银行规模找可对标路径 |

> **判断**：先看业务痛点再看技术选型，顺序反了容易陷入"为新架构找场景"。资源按用途查，比按章节顺序读更省时间。

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

## 主机时代技术栈与语言科普

> 以下两篇为主体技术栈的历史科普，帮助理解"集中式单体为何稳定却封闭"与去 IOE 的由来。来源文章见各段标注。

### 主机时代的技术栈：z/OS、COBOL、DB2 与 CICS

"全国大集中"阶段依托的是一套以大型机为核心的技术栈，理解它才能理解"集中式单体"为何稳定却封闭（来源：[银行核心系统之技术架构(一)](https://mp.weixin.qq.com/s?__biz=MzIzMTk2NjAzMg==&mid=2247484164&idx=1&sn=3ca38e06e7b2826e1f0ad37dbdf99f0a)，「小代嘚吧嘚」，2019-01）。

- **三个时代与主机特性**：主机时代 → 集群时代 → 分布式时代；主机凭强计算能力、强 I/O 与稳定安全支撑银行核心，代表特性是 Parallel Sysplex（最多 32 个 LPAR 共享读写、并行计算与恢复、可不停机动态加入集群），促成集中式单体架构——单机 + 热备可故障自动切换；冷备则需切换外设通道并重启 OS 与应用才能接管。
- **z/OS**：IBM 大型机操作系统（由 OS/390 发展而来），适合大负荷、多并发、大 I/O；地址空间分私有区域（相互隔绝）与公共区域；物理存储分实存与外存 AUX，靠页面调度移动；操作员经控制台管理；TSO 是命令输入处理器（类似 DOS），支撑 ISPF 菜单与 RMF 性能分析。
- **COBOL**：语法接近英语、格式固定、结构严谨，银行 / 保险 / 金融领域常用，一个程序修修补补可用十几年；MOVE 赋值时数值靠左对齐、字符靠右对齐。
- **DB2**：关系型数据库、OS/390 下的数据库子系统，层次为表 → 表空间 → 数据库 → 存储组，支持分布式工作单元 DUOW（两阶段提交）；分区表空间中每分区对应一个数据集与一个表、每表空间最多 254 个分区、每分区 64GB，可单独或多区处理，REORG / COPY / RECOVER 可在表空间级执行；ROWID 唯一标识记录物理位置、每表一列，可用 GENERATE ALWAYS / BY DEFAULT 生成。
- **CICS**：IBM 事务处理平台中间件，提供联机事务处理与管理，构建表述 / 业务 / 数据逻辑三层；模块含系统管理模块、系统控制表、系统控制块；关键组件有 TCP 终端管理、TCT 终端控制表、PCP 程序管理、PCT 程序控制表、KCP 任务管理、TCA 任务控制区、FCP 文件管理、FCT 文件控制表、SCP 存储管理（静态 / 动态分配）。
- **小结**：主机集中式架构简化开发测试与灾备部署、开发人员只需关注业务，但成本高且封闭；随 Java 兴起与去 IOE，国内银行逐渐接受 Java 核心，采用集群化部署与服务化架构。

### COBOL：一门"老大爷"语言的兴衰

COBOL 是主机时代的核心语言，自身也走过一条从独霸到退居二线的曲线（来源：[Cobol : 一个老大爷的自述](https://mp.weixin.qq.com/s?__biz=MzIzMTk2NjAzMg==&mid=2247483977&idx=1&sn=bc49d92f5c34a2fdcb8c0342c34f285f)，「小代嘚吧嘚」，2018-07）：

- **出身与体量**：COBOL（面向商业通用语言）50 年代末诞生，专为银行金融会计的数据收集、存储、传送、分类、排序、计算、打印而设计，主打 IBM 大机 / 中型机；因语法接近英语，90% 的 ATM 事务由其编写，代码累计超 2000 亿行且每年约增 50 亿行。
- **早期生态**：与 Fortran、FLOW-MATIC（其祖先）以及 JCL、DB2、CICS 配合，征战主机时代。
- **核心阶段演进**：2008 年后进入核心第 4 阶段（以客户为中心）；因大型机维护费高与去 IOE，业内提出"瘦核心"，把核心部署到小型机 / 开放平台（AS400、HP9000、P570），出现 Java / C/C++ / .NET 等对手。
- **语言对比**：COBOL 结构僵硬但运行高效，Java 灵活但依赖机器集群且启动慢，C/C++ 秒级启动、更省机器、效率高；COBOL 面向过程，Java / C 面向对象；中行 2017—2018 历时 9 个月完成主机下移，建成基于 X86 的分布式非金融核心，实现削峰降本。
- **现状**：Java 占优、C/C++ 尚可、.NET 不温不火，Python / PHP 受程序员欢迎，COBOL 退居二线——"老兵不死，只是凋零"。

**银行体系与机构层级**（新人基础知识）：银行分中央银行、政策性银行、国有大行、股份制、城商行、农村金融机构、村镇银行、民营银行及非银行金融机构；基本职能是信用中介与支付中介。分支机构不具法人资格、全行统一核算，层级为总行 → 一级分行 → 二级分行 → 支行 → 网点；核心系统中机构一般三到四级、各有全行唯一机构号，并区分独立核算与报账并表、实体与虚拟机构。来源：[银行业务基础知识 1](https://mp.weixin.qq.com/s?__biz=MzIzMTk2NjAzMg==&mid=2247484067&idx=1&sn=441a54041e78a3f125ec4eff32d43be6)、[银行业务基础知识 2](https://mp.weixin.qq.com/s?__biz=MzIzMTk2NjAzMg==&mid=2247484128&idx=1&sn=a6197b42e7b6991d2acac7ebdc4f7402)（「小代嘚吧嘚」，2018）。

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
| **交易回放比对** | [农行研发中心《分布式核心银行系统的测试研究与实践》（《金融电子化》2020-05）](https://mp.weixin.qq.com/s?__biz=MjM5MzA3MzAzOQ==&mid=2655478962&idx=3&sn=ec2e54f14782262d8400c2433d2b3ec0) · 神州信息 Sm@rtComplay · 华青融天 EZSonar | 生产日志脱敏回放；网络流量录制 + 旁路 TAP 镜像；**交易级 + 数据库级两层级比对** |
| **数据核对平台** | [Wallet Reconciliation（2026-08）](https://www.besthub.dev/articles/how-to-secure-wallet-funds-at-billion-scale-through-reconciliation-balance-checks-channel-matching-and-auto-repair-80148a0bdc29) · StarRocks 对账 3.0 | 采集/标准化/核对/差异中心/修复/治理六层架构；Flink SQL 分钟级差异检测 |
| **混沌工程** | [ChaosBlade](https://chaosblade.io/) · 中电金信银行核心测试方案 | 网络延迟/服务宕机/CPU 抢占故障注入，爆炸半径与自动中止安全控制 |
| **全链路压测** | 农行分布式核心性能测试实践（同上农行链接） · [dbaplus](https://www.dbaplus.cn) | JMeter 单交易基准/负载/混合/稳定场景；类网关统一发压；80% 交易量在 20% 时间内完成推算 TPS |
| **信创适配测试** | [twt：信创数据库核心迁移性能瓶颈应对](https://www.talkwithtrend.com/Question/475851) · 《信创选型实战指南》 | 「主动施压、全链路透视、分层治理」；分片键前置设计；基准性能画像 + APM；脱敏回放 + 混沌演练 |

> **判断**：单靠功能测试用例不足以覆盖分布式核心切换风险；应把**交易回放比对、数据一致性核对、混沌演练、全链路压测**作为一套完整方法体系写入迁移方案（见 [migration.md](migration.md)）。
