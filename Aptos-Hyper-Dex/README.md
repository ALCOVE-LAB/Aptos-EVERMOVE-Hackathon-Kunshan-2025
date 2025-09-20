# Aptos-Hyper-dex - 基于 Aptos 的去中心化永续合约交易所

## 项目名称
**Aptos-Hyper-dex** - 高性能去中心化永续合约交易平台

## 项目描述

HyperPerp 是一个基于 Aptos 区块链构建的去中心化永续合约交易所，采用**链下撮合 + 链上结算**的混合架构设计。项目解决了传统中心化交易所的信任问题，同时通过链下撮合引擎实现了高性能的交易体验。

### 核心功能
- **永续合约交易**：支持 BTC、ETH 等主流资产的永续合约交易(测试网)
- **链下撮合引擎**：基于 Rust 的高性能订单撮合系统
- **链上资金管理**：使用 Move 智能合约确保资金安全
- **风险管理系统**：包含保证金管理
- **现代化前端**：基于 Next.js 的响应式交易界面

### 解决的问题
1. **信任问题**：通过区块链技术实现去中心化，用户资金由智能合约托管
2. **性能问题**：链下撮合 + 链上结算的架构平衡了安全性和性能
3. **用户体验**：提供类似中心化交易所的流畅交易体验
4. **资金安全**：所有资金操作都在链上执行，透明可审计

## Aptos 区块链集成

### Move 智能合约模块
项目充分利用了 Aptos 的 Move 语言特性，构建了完整的永续合约系统：

- **`perp_engine`**：永续合约引擎，处理批量结算和交易执行
- **`vault_coin`**：资金托管金库，使用 Aptos Coin 标准管理 USDC
- **`positions`**：持仓管理模块，跟踪用户的多空仓位
- **`account`**：用户账户管理，包含抵押品和未结算 PnL
- **`oracle_adapter`**：价格预言机适配器，支持多种价格源
- **`market_registry`**：市场参数管理，支持动态添加交易对
- **`liquidation`**：清算机制，自动处理风险仓位
- **`events`**：事件系统，记录所有交易和状态变化
- **`gov`**：治理模块，支持多签和权限管理

### 链上交互特性
- **批量结算**：通过 `apply_batch` 函数实现高效的批量交易结算
- **事件监听**：利用 Aptos 事件系统实现实时状态更新
- **资源管理**：使用 Move 的资源模型确保资金安全
- **权限控制**：基于 Aptos 账户模型的细粒度权限管理

## 技术栈


### 前端技术
- **框架**：Next.js 14.2.3 + React 18
- **UI 库**：Radix UI + Tailwind CSS

### 后端技术
- **匹配引擎**：Rust + Tokio 异步运行时
- **数据库**：PostgreSQL + SQLx ORM
- **API 框架**：Axum Web 框架
- **缓存**：Redis（可选）
- **消息队列**：Tokio Channels


### 区块链技术
- **智能合约**：Move 语言
- **区块链**：Aptos 测试网
- **开发工具**：Aptos CLI + Aptos SDK
- **索引器**：Rust

## 安装与运行指南

### 环境要求
- Node.js 18+ 
- Rust 1.75+
- PostgreSQL 14+
- Aptos CLI

### 快速开始

#### 1. 克隆项目
```bash
git clone https://github.com/your-username/aptos-hyper-dex.git
cd aptos-hyper-dex
```

#### 2. 部署智能合约
```bash
cd move/contracts/hyperperp
# 安装依赖
npm install

# 运行测试
npm run test

# 部署到测试网
./sh_scripts/deploy.sh
```

#### 3. 启动匹配引擎
```bash
cd rust-matching-engine

# 安装依赖
cargo build --release

# 配置环境变量
cp .env.example .env
# 编辑 .env 文件

# 启动数据库
docker-compose up -d postgres

# 运行匹配引擎
cargo run
```

#### 4. 启动前端应用
```bash
cd next-app

# 安装依赖
npm install

# 启动开发服务器
npm run dev
```

#### 5. 启动索引器（可选）
```bash
# Rust 版本（生产环境推荐）
cd rust-indexer
cargo run --release

# TypeScript 版本（开发环境）
cd ts-indexer
npm start
```

### 详细配置

#### 环境变量配置
```bash
# 数据库配置
DATABASE_URL=postgresql://username:password@localhost:5432/hyperperp

# Aptos 配置
APTOS_NODE_URL=https://fullnode.testnet.aptoslabs.com/v1
APTOS_ADMIN_ADDRESS=0x...
APTOS_CONTRACT_ADDRESS=0x...

# 服务器配置
SERVER_HOST=127.0.0.1
SERVER_PORT=8080
```

#### 钱包配置
1. 登录交易所(Aptos-Hyper-dex)
2. 自动连接到 Aptos 测试网
3. 通过部署 [Mint-Cypto-Testnet](https://github.com/Aptos-Hyper-Dex/Mint-Cypto-Testnet) 获取测试代币 USDC。 

## 项目亮点/创新点

### 1. 混合架构设计
- **链下撮合**：实现毫秒级订单匹配，支持高并发交易
- **链上结算**：确保资金安全和交易不可篡改
- **最佳平衡**：兼顾性能和去中心化特性

### 2. 高性能匹配引擎
- **内存订单簿**：基于 BTreeMap 的高效订单管理
- **价格时间优先**：标准交易所撮合算法
- **批量结算**：减少链上交易费用和延迟
- **事件驱动**：实时交易状态更新

### 3. 完整的风险管理系统
- **动态保证金**：支持不同资产的差异化保证金要求

### 4. 现代化开发体验
- **类型安全**：端到端 TypeScript 支持
- **实时更新**：WebSocket 连接实现实时数据同步
- **响应式设计**：支持桌面和移动端交易
- **开发者友好**：完整的测试套件和文档

### 5. 可扩展的架构
- **模块化设计**：各组件独立部署和扩展
- **多链支持**：架构支持扩展到其他区块链
- **插件系统**：支持自定义订单类型和交易策略

## 未来发展计划

### 短期目标
- **自动清算**：实时监控仓位风险，自动触发清算
- **价格保护**：防止价格操纵和异常交易
- **多层验证**：交易前、中、后的多重风险检查
- **主网部署**：完成 Aptos 主网部署和审计
- **更多交易对**：支持 ETH、SOL 等主流资产
- **移动端应用**：开发原生移动端交易应用
- **API 开放**：提供公开 API 供第三方集成

### 中期目标
- **高级订单类型**：支持止损、止盈、冰山订单等
- **社交交易**：支持跟单和策略分享
- **机构服务**：提供机构级交易和风控工具

### 长期愿景
- **去中心化治理**：实现完全去中心化的协议治理
- **Layer 2 集成**：支持 Aptos 的 Layer 2 解决方案
- **衍生品扩展**：支持期权、期货等更多衍生品
- **生态建设**：构建完整的 DeFi 生态系统

## 团队成员

Chacha @chachaxw
CryptoTyson @debugzhao
timerring @timerring

## 演示视频/截图

### 功能截图

![](./orderbook.png)

![](./orders.png)


1. **交易界面**：现代化的订单簿和交易面板
2. **持仓管理**：实时持仓监控和风险管理
3. **资金管理**：安全的存款和提款流程
4. **移动端适配**：响应式设计支持各种设备

### 技术演示（线下展示）
- **交易流程演示**：完整的开仓到平仓流程
- **性能测试**：高并发交易的压力测试结果


---

**Aptos-Hyper-dex** - 构建下一代去中心化衍生品交易平台 🚀
