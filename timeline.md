# 分布式核心银行发展时间线（2014—2026）

> 按时间轴组织 [cases.md](cases.md)、[databases.md](databases.md)、[papers.md](papers.md)、[vendors.md](vendors.md) 中的事件，覆盖 2014—2024 年的历史脉络。
>
> **来源标注**：`一手` = 官方/厂商官网/官方署名；`权威二手` = 权威媒体/研究报告；`待核实` = 仅搜索摘要命中。年份以公开披露为准，不同来源对「立项/投产/全面投产」口径可能不同。

## 一览：四个阶段的演进主线

| 阶段 | 时间 | 关键词 | 标志性事件 |
|---|---|---|---|
| **政策驱动 + 起步** | 2014—2018 | 去 IOE、39 号文、互联网银行 | 银监会 39 号文（2014）；微众/网商全分布式核心；GoldenDB 立项（2014）；OceanBase 上支付宝核心账务（2016） |
| **核心首例突破** | 2019—2021 | 信用卡核心 → 账务核心 | 中信信用卡核心（2019-10）+ 账务核心（2020-05）；张家港农商行首例（2019-08）；OceanBase 两次登顶 TPC-C |
| **规模化推广** | 2022—2024 | 信创三期、大行全面改造 | 邮储个人核心（2022-04）+ 公司核心（2024）；金融科技发展规划二期（2022-01）；金融信创三期试点 |
| **主机收官 + AI 化** | 2025—2026 | 去主机、AI 原生、湖库一体 | 工行/农行/建行/中行同年完成主机下移；国产库全面转向 AI 原生；国际核心 AI 辅助 COBOL 迁移 |

## 2014—2018：政策驱动与起步期

### 政策与行业背景

| 时间 | 事件 | 来源 | 标注 |
|---|---|---|---|
| 2008—2013 | 阿里提出并实施「去 IOE」：2008 王坚提出，2009 全面启动，2012 年底淘宝系去 IOE 完成，2013-05-17 支付宝最后一台 IBM 小型机下线，2013 年 EMC 存储全部下线 | [财新/ CSDN 转载《去IOE真相》](https://mp.weixin.qq.com/s?__biz=Mzg4MjYzMjI1MA==&mid=2247515811&idx=1&sn=f279dd58400209b9a13c8cb886580308) | 权威二手 |
| 2013 | 棱镜门事件，信息安全上升到国家安全高度，金融信创的直接催化剂 | [移动支付网《蚂蚁的幸运》](https://m.mpaypass.com.cn/news/202008/27090240.html) | 权威二手 |
| **2014** | **银监会等四部委《关于应用安全可控信息技术、加强银行业网络安全和信息化建设的指导意见》（39 号文）**：要求自 2015 年起安全可控技术应用比例逐年不低于 15%，到 2019 年总体达 75% 左右 | [新华财经研报](https://thinktank.cnfin.com/yxyyj-lb/detail/20240326/4027628_1.html) · [中银协高峰演讲](https://fintechinchina.com/cases/4305) | 权威二手 |
| 2016 | 《中国银行业信息科技发展"十三五"规划》：提出探索利用云服务平台开展金融核心业务，「十三五」末面向互联网场景的重要信息系统全部迁移到云架构，其他系统迁移比例不低于 60% | [新华财经研报](https://thinktank.cnfin.com/yxyyj-lb/detail/20240326/4027628_1.html) | 权威二手 |

### 银行与产品里程碑

| 时间 | 事件 | 来源 | 标注 |
|---|---|---|---|
| 2014 年底 | **微众银行搭建全国银行业第一个完全通过安全可控技术实现的全分布式架构**，国内首个建成「去 IOE」科技系统架构的银行；X86 标准 PC 服务器 + 深度定制开源技术 | [界面新闻《微众银行"去IOE"背后的故事》](https://www.jiemian.com/article/1074967.html) | 权威二手 |
| 2014 | **GoldenDB 在中兴通讯内部立项**，目标直指金融行业核心交易型分布式数据库；与中信银行（「天使客户」）联合研发 | [人民日报（2024-03-05）](https://paper.people.com.cn/rmrb/html/2024-03/05/nw.D110000renmrb_20240305_1-19.htm) · [新华网（2023-06）](https://www.news.cn/info/20230630/6388002f6b2346e1ab70f718dd618078/c.html) | 一手 |
| 2014 | OceanBase 取代 Oracle 支撑支付宝核心交易系统，承担双十一 10% 交易流量，首次实现 RPO=0 / RTO<30s | [OceanBase 官网里程碑](https://www.oceanbase.com/about) | 一手 |
| 2015 | **网商银行开业**，首家搭建在去 IOE 银行核心业务系统上的商业银行，全部核心交易库运行在 OceanBase；同年 OceanBase 承担双十一 100% 交易流量 | [中国网财经（2015-05）](https://finance.china.com.cn/money/efinance/yw/20150520/3128819.shtml) · [OceanBase 官网](https://www.oceanbase.com/about) | 一手 + 权威二手 |
| 2015-05 | 微众银行首款产品「微粒贷」上线，分布式架构经受第一次海量交易并发实战 | [界面新闻](https://www.jiemian.com/article/1074967.html) | 权威二手 |
| 2016 | **OceanBase 1.0 发布**：重新设计架构，支持分布式事务与多租户；上线支付宝核心账务、核心支付系统，**全球首次使用分布式数据库支撑金融核心账务系统**，支撑 12 万笔/秒支付峰值 | [OceanBase 官网](https://www.oceanbase.com/about) · [官方文档](https://en.oceanbase.com/docs/common-oceanbase-database-10000000001029033) | 一手 |
| 2017 | OceanBase 完成蚂蚁集团核心系统最后一个 Oracle 替换；**南京银行成为首家上线用户**（首次对外商业化）；双十一 4200 万次/秒处理峰值 | [OceanBase 官网](https://www.oceanbase.com/about) | 一手 |
| 2017-10-16 | **TiDB 1.0 正式发布**，开源分布式 HTAP 数据库生产就绪，亚太 30+ 家企业生产部署 | [PingCAP 官方博客](https://pingcap.com/blog/announcing-tidb-1.0-release) | 一手 |
| 2018-03 | 北京银行上线分布式数据库，采用**两地三中心五副本**架构；同年 5 月互联网银联清算平台、6 月银联无卡支付平台投产——早期城市商业银行分布式核心探索代表 | [PingCAP 案例](https://www.pingcap.com/case-studies/how-bank-of-beijing-achieves-database-scaling-without-downtime) | 一手（厂商） |
| 2018 | OceanBase V2.0 发布，引入 **Oracle 兼容模式**，降低外部客户应用改造成本 | [OceanBase 官方文档](https://en.oceanbase.com/docs/common-oceanbase-database-10000000001029033) | 一手 |

## 2019—2021：核心首例突破期

### 银行案例

| 时间 | 事件 | 来源 | 标注 |
|---|---|---|---|
| 2019-06 | GoldenDB 以 50 项测评全部满分通过工信部信通院「大数据产品能力测评」分布式事务数据库能力认证，成为首个满分厂商 | [中国日报网](https://ex.chinadaily.com.cn/exchange/partners/82/rss/channel/cn/columns/sz8srm/stories/WS6551bca0a310d5acd876e90e.html) | 权威二手 |
| 2019-08 | **张家港农商行新一代核心投产**（TDSQL + 长亮），国内银行业首家在传统核心中采用国产分布式数据库的商业银行 | [张家港农商行官网](https://www.zrcbank.com/news/details_532_2374.html) | 一手 |
| **2019-10-26** | **中信银行新一代信用卡核心（StarCard）投产**，1 亿用户数据从 DB2 迁移到 GoldenDB；双十一线上交易额 2 分钟破 1 亿、1 小时破 10 亿，系统交易速度提升 3 倍 | [新华网（2023-06）](https://www.news.cn/info/20230630/6388002f6b2346e1ab70f718dd618078/c.html) · [中国日报网](https://ex.chinadaily.com.cn/exchange/partners/82/rss/channel/cn/columns/sz8srm/stories/WS6551bca0a310d5acd876e90e.html) | 一手 + 权威二手 |
| 2019-08 | 央行公布首轮《金融科技（FinTech）发展规划（2019—2021 年）》，提出构建集中式与分布式协调发展的信息基础设施架构 | [中国政府网（2022-01 报道）](https://www.gov.cn/zhengce/2022-01/07/content_5666817.htm) | 一手 |
| **2020-05-03** | **中信银行「凌云」账务核心投产**：国内首个在大型银行账务核心投产的国产数据库（GoldenDB）；3 亿客户 / 15 亿账户，每秒交易超 2 万笔；RPG2JAVA 代码翻译 + 仿真比对工具，新老系统 24 个月同步研发发版 | [中信银行官网](https://echannel.citicbank.com/about/companynews/banknew/message/202008/t20200804_87237.html) · [新华网](https://www.news.cn/info/20230630/6388002f6b2346e1ab70f718dd618078/c.html) | 一手 |
| 2020-06 | GoldenDB 在银联数据信用卡核心投产，1.5 亿卡用户规模下 TPS 实测超 10 万（当时业内金融核心实际业务环境最大数值） | [中国日报网](https://ex.chinadaily.com.cn/exchange/partners/82/rss/channel/cn/columns/sz8srm/stories/WS6551bca0a310d5acd876e90e.html) | 权威二手 |
| 2020-10 / 11 | GoldenDB 相继在赣州银行信贷及核算核心、贵州银行核心投产 | [中兴 GoldenDB 官方彩页（PDF）](https://www.zte.com.cn/content/dam/zte-site/res-www-zte-com-cn/mediares/zte/zhengqi/finance/ziliao_xiazai/GoldenDB-.pdf) | 一手 |
| 2020 | **金融信创一期试点启动**：47 家机构（头部银行保险券商、一行两会、交易所），信创基础软硬件采购占 IT 外采 5—8% | [头豹研究院](https://www.leadleo.com/wiki/brief/62c528cee7ced6cb6ef0f75b) | 权威二手 |
| 2021-06 / 12 | GoldenDB 完成中国移动全网客户中心系统（06）、助力建设银行核心业务架构转型（12） | [新华网（2023-06）](https://www.news.cn/info/20230630/6388002f6b2346e1ab70f718dd618078/c.html) | 一手 |
| 2021 | **金融信创二期试点**：198 家机构，OA/邮件全部替换，信创基础软硬件占 IT 外采提高至 8—15% | [头豹研究院](https://www.leadleo.com/wiki/brief/62c528cee7ced6cb6ef0f75b) | 权威二手 |

### 数据库产品里程碑

| 时间 | 事件 | 来源 | 标注 |
|---|---|---|---|
| 2019 | **OceanBase 首次参加 TPC-C**，2.2 版本以 6088 万 tpmC 登顶，打破 Oracle 保持 9 年的世界纪录；双十一创造 6100 万次/秒处理峰值 | [OceanBase 官网](https://www.oceanbase.com/about) | 一手 |
| 2019-05-15 | **华为正式发布 GaussDB**，定位全球首款 AI-Native 数据库 + 首款基于鲲鹏的企业级数据库 | [华为官方 PDF](https://www-file.huawei.com/dam/asset/view/16e454a6db99405383c30ddabe33e534.pdf) · [百科时间线](https://baike.com/wikiid/7000988911129171232) | 一手 + 二手 |
| 2019-09 | 华为宣布开源 GaussDB 单机版，命名 openGauss | [百科时间线](https://baike.com/wikiid/7000988911129171232) | 二手 |
| **2020** | **OceanBase 成立公司（北京奥星贝斯）独立商业化运作**，TPC-C 7.07 亿 tpmC 打破自己保持的世界纪录，超 Oracle 23 倍 | [OceanBase 官网](https://www.oceanbase.com/about) | 一手 |
| 2020-06-30 | **openGauss 正式开源**，源码对外开放 | [百科时间线](https://baike.com/wikiid/7000988911129171232) · [Wikiwand](https://www.wikiwand.com/en/GaussDB) | 二手 |
| 2020-08 | 华为将 GaussDB 并入华为云 | [百科时间线](https://baike.com/wikiid/7000988911129171232) | 二手 |
| 2021-06-01 | **OceanBase 正式开源**，开放 300 万行核心代码（SQL/事务/存储引擎），采用 Open Core 模式 | [OceanBase 官网](https://www.oceanbase.com/about) · [官方文档](https://en.oceanbase.com/docs/common-oceanbase-database-10000000001029033) | 一手 |
| 2021 | OceanBase V3.0 以 TPC-H 1526 万 QphH@30000GB 登顶，成为全球唯一同时登顶 TPC-C 与 TPC-H 的分布式数据库；客户数突破 400 家 | [OceanBase 官网](https://www.oceanbase.com/about) | 一手 |
| 2021-03 / 07 | openGauss 2.0.0 上线（03）；华为云 GaussDB 推出 Ustore 存储引擎（07） | [百科时间线](https://baike.com/wikiid/7000988911129171232) | 二手 |

## 2022—2024：规模化推广期

| 时间 | 事件 | 来源 | 标注 |
|---|---|---|---|
| **2022-01** | 央行印发**《金融科技发展规划（2022—2025 年）》**（第二轮）：明确 4 基本原则、6 目标、8 项重点任务、5 项保障；提出稳妥推进信息系统向多节点并行、数据分布存储、动态负载均衡的分布式架构转型，敏态与稳态双模并存 | [中国政府网](https://www.gov.cn/zhengce/2022-01/07/content_5666817.htm) | 一手 |
| **2022-04** | **邮储银行新一代个人业务核心全面投产**：基于鲲鹏硬件 + openGauss 开源数据库 + GaussDB 分布式云数据库，6 亿+ 个人客户在线无感迁移 | [邮储银行官网](https://www.psbc.com/cn/gyyc/ycfm/ycdt/202204/t20220425_177060.html) · [百科](https://baike.com/wikiid/7000988911129171232) | 一手 |
| 2022 | **金融信创三期试点启动**，计划扩容至全行业 5000+ 家金融机构，覆盖部分重要核心系统，信创基础软硬件占 IT 外采比例望提高至 15—25% | [头豹研究院](https://www.leadleo.com/wiki/brief/62c528cee7ced6cb6ef0f75b) | 权威二手 |
| 2022 | **OceanBase 4.0 发布**，正式发布公有云，提出「单机分布式一体化」 | [OceanBase 官网](https://www.oceanbase.com/about) | 一手 |
| 2022-08 | GaussDB 内核获 CC EAL4+ 安全认证；国泰君安核心交易系统上线 GoldenDB（支撑 1500 万账户） | [百科](https://baike.com/wikiid/7000988911129171232) · [新华网](https://www.news.cn/info/20230630/6388002f6b2346e1ab70f718dd618078/c.html) | 二手 + 一手 |
| 2023-01 | 「建行云」在北京正式发布，率先实现「多功能区、多地域、多技术栈、多种芯片」四多布局，算力规模提升超 30% | [新华财经研报](https://thinktank.cnfin.com/yxyyj-lb/detail/20240326/4027628_1.html) | 权威二手 |
| 2023-06-07 | 华为全球智慧金融峰会发布**新一代分布式数据库 GaussDB**（全流程软硬件协同） | [百科时间线](https://baike.com/wikiid/7000988911129171232) | 二手 |
| 2023-06 | GoldenDB 助力工商银行启动对公核心业务系统切流，容器化部署实现超大规模集群 | [人民日报（2024-03-05）](https://paper.people.com.cn/rmrb/html/2024-03/05/nw.D110000renmrb_20240305_1-19.htm) | 一手 |
| 2023 / 2024 | 广发银行 GoldenDB 分布式银行核心（2023）+ 信用卡核心（2024，超 1.2 亿卡客户）；建设银行对私核心（GoldenDB，2024） | 见 [cases.md](cases.md) | 一手 |
| 2024-01 / 10 | 邮储银行新一代公司业务核心投产（01）/ 全量客户迁移收官（10），软硬件 100% 国产化 | 见 [cases.md](cases.md) | 一手 |
| 2024-09 | 招商银行首家通过信通院核心系统现代化建设水平评估（「优秀级+」）；浦发信用卡分布式核心一次性切换投产 | 见 [cases.md](cases.md) | 二手 |
| 2024-03 | 人民日报披露 GoldenDB 已应用 60 余家金融机构，申请专利超 500 件，银行核心稳定运行超 4 年 | [人民日报](https://paper.people.com.cn/rmrb/html/2024-03/05/nw.D110000renmrb_20240305_1-19.htm) | 一手 |
| 2024-05-06 | 华为云发布 GaussDB 基础版 | [百科](https://baike.com/wikiid/7000988911129171232) | 二手 |

## 2025—2026：主机收官与 AI 化

> 详细内容见 [cases.md](cases.md)、[databases.md](databases.md)、[vendors.md](vendors.md)、[papers.md](papers.md)，此处仅列主线。

| 时间 | 事件 |
|---|---|
| 2025-04 | 农业银行完成银行业规模最大主机切换下线；英格兰银行 RTGS 新核心 RT2 上线 |
| 2025-05 | 华为发布分布式新核心解决方案 5.5；TDSQL 一体化版本发布（多引擎统一管控） |
| 2025-07 | 腾讯云《商业银行核心系统分布式转型白皮书》发布；PolarDB TPC-C 20.55 亿 tpmC |
| 2025-09 | 中信「银河项目」投产；TDSQL 3.0 家族发布 |
| 2025-10 | 国家开发银行新资金系统投产（OceanBase 替代 Oracle）；贵州农信新一代核心投产 |
| 2025-11-07 | **工商银行最后一台主机关停**，全面完成从主机集中式向「云原生 + 分布式」转型 |
| 2025-11-15 / 12-24 | 四川农商联合银行新一代分布式核心投产 / 大机下电，首家实现大机下电的省级农商行 |
| 2025-12 | 中国银行史上最大规模批次投产（25 部门 / 37 境内 / 15 境外 / 54 外联方，欧非 13 分行） |
| 2025 全年 | Thought Machine 营收破 1 亿美元（+57%）；Oracle / TCS BaNCS / Backbase 密集发布 AI Agent 核心能力 |
| 2026 | 建行境内外全部核心主机下移收官；省级农信换芯规模化复制；国产库全面转向 AI 原生（湖库一体/向量/库内 AI）；Thought Machine + AWS 推出 COBOL → Python 的 AI 迁移管线 |

## 国际脉络（2014—2024）对照

| 时间 | 事件 | 来源 | 标注 |
|---|---|---|---|
| 2015 | 欧盟通过 **PSD2《支付服务指令第二版》**，2018-01-13 正式实施，引入 AISP/PISP 与开放银行模式；强客户认证 2019-09-14 起实施 | [PSD2 百科](https://baike.baidu.com/item/PSD2/67382101) | 二手 |
| 2016 | Thought Machine 成立；英国 Open Banking 成立 | [Thought Machine 官网](https://www.thoughtmachine.net/our-story) | 一手 |
| 2018-03 | SWIFT 宣布 ISO 20022 迁移计划，MT→MX 共存期 2023—2025，2025-11 核心切换（MT102/103/201/203 被拒收），部分附属报文延至 2027-11 | [Electronic Payments International](https://www.electronicpaymentsinternational.com/?p=82628) · [HSBC](https://www.business.hsbc.com/en-gb/campaigns/iso20022) | 权威二手 |
| 2020—2021 | 云原生核心概念兴起，SaaS 化核心成为国际主线（Temenos SaaS、Thought Machine Vault、Mambu） | 见 [vendors.md](vendors.md) | — |
| 2025-11 | PSD3 / 支付服务法规（PSR）达成临时政治协议，2026-04 COREPER 认可最终文本，预计 2027 生效 | [Open Banking Tracker](https://www.openbankingtracker.com/guides/commercial-open-banking-standards) | 权威二手 |

> **中外对照**：国内主线是「政策驱动 + 信创自主可控 + 主机下移」，国际主线是「监管开放（PSD2/Open Banking）+ 云原生核心 + SaaS 化」。两者在 2025—2026 汇合于 AI 原生数据库与智能体化核心。

## 关键判断

1. **2014 年是真正的起点**：39 号文（政策）+ 微众全分布式架构（技术）+ GoldenDB 立项（产业）三件事同年发生，此后十年的主线都在这一年埋下伏笔。
2. **「信用卡核心 → 账务核心」是通用路径**：中信 2019→2020、广发 2023→2024、浦发 2024→2025，都遵循先在信用卡（相对独立、容错空间大）验证，再攻总账 core 的规律。
3. **数据库厂商的「天使客户」模式**：GoldenDB 之于中信、OceanBase 之于网商/支付宝、GaussDB 之于工行/招行——金融核心级数据库不是靠 benchmark 卖出来的，是靠 5—6 年联合研发 + 长期稳定运行时长换来的信任。
4. **政策节奏决定行业节奏**：39 号文（2014）→ 十三五（2016）→ FinTech 规划一期（2019）→ 二期（2022）；金融信创一/二/三期试点（2020/2021/2022）。每一轮政策都对应一波银行核心改造高峰。
5. **TPC-C 是「入场券」而非「终点」**：OceanBase 2019/2020 两次登顶、TDSQL 2024 8.14 亿 tpmC、PolarDB 2025 20.55 亿 tpmC，但真正的落地标准是「核心系统稳定运行年限 + 零事故」——GoldenDB 中信 6 年、OceanBase 支付宝 10 年。
