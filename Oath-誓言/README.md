# 誓言（OATH）— Aptos 原生链上信用协议（Hackathon 概念介绍）

## 一句话介绍
**OATH** 将“承诺”资产化：用可验证的链上凭证与经济抵押，建立项目方与投资者之间的原生链上信用，先从 **Aptos DeFi** 冷启动，逐步扩展到链上/链下的所有履约场景。

## 痛点与机会
- **Rug Pull 与信息不对称**：投资者难以识别真实可执行的承诺，违约成本低。
- **信用不可迁移**：在单一协议内形成的信誉，难以跨协议/跨场景复用。
- **缺少标准化的履约凭证**：链上缺乏可组合的“承诺→履约→增信”的标准化资产。

## OATH 的核心方案
- **承诺资产化**：用户/项目方创建“誓言（Vow）”，锁定抵押品，承诺目标（如 APY、里程碑）。
- **链上凭证**：履约完成自动铸造 **SBT/凭证**，形成可组合、可迁移的链上信用历史。
- **可验证与仲裁**：接入 **Switchboard** 等预言机，结合链上/链下证据（Arweave/IPFS）实现可裁决流程。
- **DeFi 场景切入**：与类 **MetaMorpho** 的借贷/收益优化 Vault 协同，作为“信用增强层”吸引资金流入。

## 技术栈与合约信息（Aptos）
- **前端**：Next.js + React + TypeScript + Tailwind CSS（配合 Recharts 数据可视化）
- **钱包**：Petra / Martian（Aptos Wallet Adapter 或 `window.aptos`）
- **SDK**：`@aptos-labs/ts-sdk`（测试网交互）
- **预言机**：Switchboard（APY/价格/里程碑验证，Hackathon 可脚本模拟）
- **存储**：链上哈希 + Arweave/IPFS（原始证据/材料）
- **合约（Testnet）**：
  - 地址：`0xa3228904a096599a799b74cb18ddd0eb0a78e49c07c119b80d597c804476b0e0`
  - 模块：`oath`
  - 关键函数：`create_oath`、`get_oath`、`complete_oath_and_mint_sbt`、`get_sbt`

## 产品形态（MVP）
- **Landing**：核心指标（Total Value Vowed、Active、Fulfilled、Broken），入口（Explore / Make a Vow）。
- **誓言市场**：按抵押价值、到期、类型、状态筛选；卡片化展示信誉可视化。
- **创建誓言**：模板化（APY承诺/里程碑/Token Lock 等），多 Token 抵押，钱包签名提交。
- **详情页**：链上状态、交易历史、抵押、证据与仲裁、APY/TVL 实时图表（Switchboard）。
- **Vault 集成**：支持基金管理者创建带抵押的 APY 誓言，吸引投资者存入 USDC（移除 shares 概念，以金额占比衡量权益）。

## 商业与生态
- **收入**：协议费（1–2%）、仲裁服务费（~1%）、高级功能（信誉评分/API、白名单、风控套件）。
- **价值**：作为 Aptos 生态的**信用基础设施**，沉淀跨场景可复用的履约数据与信誉网络。
- **扩展**：从 DeFi → DAO 交付、GameFi 赛事、供应链履约、自由职业交易等链上/链下场景。

## 里程碑（Hackathon 版本）
- ✅ 前端框架与 UI（TS + Next.js + Tailwind）
- ✅ 钱包连接与基本交易流（Petra/Martian）
- ✅ 誓言创建/浏览/详情页面（含模拟数据与图表）
- ✅ Vault 市场与详情（类 MetaMorpho 交互逻辑的 Aptos 化）
- 🔜 预言机接入与自动仲裁流程（Switchboard Testnet/脚本模拟）
- 🔜 信誉评分与可组合接口（SBT+API）

## 团队信息
- **smiley**（前端/架构）：概念提出者、Next.js/TS 架构、钱包与图表、交互体验。
- **志明**（Move/合约 & 后端）：Aptos 合约、预言机与验证逻辑、交易流程。
- **jeff**（产品与生态 BD）：场景梳理、商业化策略、生态合作。

## 开源仓库与参考
- **代码库**：[`TheDAS-designer/oath_defi`](https://github.com/TheDAS-designer/oath_defi.git)
- 参考与说明：
  - Aptos & TS SDK、Wallet Adapter 集成（仓库前端部分）
  - 合约模块与 CLI 交互脚本（`contract/` 与 `tests/`）

> 更多细节与 Demo 请参考仓库 README 与 `frontend/` 目录，或联系我们获取演示环境与测试钱包。

—— 让承诺可验证，让信用可复用。 