# 核心概念

## Core Banking（核心银行系统）

银行用来支撑最基础业务运转的后台核心系统，是银行的"总账本 + 发动机"。

### 功能范围

- **客户与账户管理**：开立储蓄卡、信用卡、存款账户，维护客户信息
- **存款业务**：活期、定期、利息计算与结息
- **贷款业务**：放款、还款计划、利息计提
- **支付结算**：转账、跨行清算、代收代付
- **总账与会计**：所有交易入账，产出日终账务、对账单

### 关键特征

| 特征 | 说明 |
|---|---|
| 集中性 | 全行统一的一套系统，而非每个网点各一套 |
| 7×24 运行 | 支持日终批处理（batch）与实时交易 |
| 强一致性 | 余额、账务必须绝对准确 |
| 高稳定性 | 宕机即全行业务停摆 |

### 概念辨析

- Core Banking ≠ 手机银行、网银（后者是"渠道层"前台）
- Core Banking ≠ 信贷系统、反洗钱系统（外围专业系统，通过接口对接）

## 集中式 vs 分布式架构

| 维度 | 传统集中式核心 | 分布式核心 |
|---|---|---|
| 硬件 | IBM 大型机 / 小型机 | x86 普通服务器集群 |
| 数据库 | Oracle、DB2 | 分布式数据库 |
| 应用架构 | 单体应用 | 微服务（Dubbo / Spring Cloud） |
| 扩展方式 | Scale-up（换更大机器） | Scale-out（水平加节点） |
| 可用性 | 单点，依赖主机高可靠 | 多副本，单点故障可自动接管 |
| 成本 | 软硬件昂贵，受制于供应商 | 普通硬件，自主可控 |

## 分布式化的驱动力

1. **扩展瓶颈**：移动银行与支付峰值（如双十一）流量增长，集中式只能垂直扩容，成本指数上升
2. **单点风险**：主机故障即全行停摆
3. **信创 / 去 IOE**：国产化替代政策，摆脱对 IBM / Oracle / EMC 的依赖

## 术语对照

| 中文 | 英文 |
|---|---|
| 核心银行系统 | Core Banking System |
| 分布式核心 | Distributed Core Banking (System) |
| 核心系统改造 | Core Banking Transformation / Migration |
| 云原生核心 | Cloud-Native Core Banking |
| 信创 | IT Application Innovation（国产化替代） |
| 去 IOE | De-IOE（去 IBM / Oracle / EMC） |
| 异地多活 | Multi-Site Active-Active |
| 日终批处理 | End-of-Day (EOD) Batch Processing |
| 灰度切流 | Gradual Traffic Cutover / Canary Rollout |
