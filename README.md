# uniapp-web3-starter 🚀

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![uniapp](https://img.shields.io/badge/uni--app-framework-brightgreen)](https://uniapp.dcloud.net.cn/)
[![web3](https://img.shields.io/badge/Web3.js-ethers.js-blue)](https://docs.ethers.org/v6/)

一个基于 UniApp 和 ethers.js 的 Web3 入门模板项目，帮助开发者快速构建支持多端的去中心化应用（DApp）。

## ✨ 功能特性

- ✅ **多端支持**: 基于 UniApp，一套代码可发布到 iOS、Android、Web 以及各种小程序平台
- ✅ **钱包连接**: 轻松连接 MetaMask 等以太坊钱包
- ✅ **余额查询**: 查询账户 ETH 余额
- ✅ **响应式设计**: 适配不同屏幕尺寸
- ✅ **简洁架构**: 代码结构清晰，易于理解和扩展

## 🛠 技术栈

- [UniApp](https://uniapp.dcloud.net.cn/) - 跨平台应用开发框架
- [Vue 3](https://v3.vuejs.org/) - 渐进式 JavaScript 框架
- [ethers.js v6](https://docs.ethers.org/v6/) - 完整的以太坊钱包实现和实用工具
- [MetaMask](https://metamask.io/) - 以太坊钱包和 DApp 网关

## 📦 安装与使用

### 前置条件

- Node.js (版本 14.x 或更高)
- npm 或 yarn 包管理器
- HbuilderX (推荐) 或 Vue CLI
- 浏览器中安装 MetaMask 钱包

### 快速开始

1. **克隆项目**
   ```bash
   git clone https://gitee.com/你的用户名/uniapp-web3-starter.git
   cd uniapp-web3-starter
   
2. **安装依赖**
   ```bash
   npm install
   
3. **运行项目**
   ```bash
   # 使用 HbuilderX 打开项目并运行
   # 或使用 Vue CLI 运行到 H5 平台
   npm run dev:h5
   ```
4. **访问应用**

- 在浏览器中打开 HbuilderX 提供的本地地址 (通常是 `http://localhost:8080`)
- 点击"连接钱包"按钮
- 授权 MetaMask 连接请求
- 查看你的钱包地址和 ETH 余额

## 🎯 项目结构

text

```
uniapp-web3-starter/
├── pages/                 # 页面文件目录
├── static/               # 静态资源目录
├── App.vue              # 主应用组件
├── main.js              # 应用入口文件
├── manifest.json        # 应用配置文件
└── package.json         # 项目依赖配置
```



## 🤝 如何贡献

我们欢迎任何形式的贡献！以下是参与步骤：

1. Fork 本项目
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 开启一个 Pull Request

请阅读 [CONTRIBUTING.md](CONTRIBUTING.md) 了解详细的贡献指南。

## 📄 许可证

本项目采用 MIT 许可证 - 查看 [LICENSE](https://license/) 文件了解详情。

## 🙏 致谢

- 感谢 [UniApp](https://uniapp.dcloud.net.cn/) 提供优秀的跨平台开发框架
- 感谢 [ethers.js](https://docs.ethers.org/v6/) 团队提供的出色以太坊库
- 感谢所有为开源Web3生态做出贡献的开发者

------

**提示**: 在开始使用前，请确保你的 MetaMask 钱包已安装并连接到正确的网络。
