## 概念
| Tools             |                      |
| -------------- | ---------------------- |
| **JavaScript** | 编程语言                   |
| **Node.js**    | 让 JS 能在电脑 / 服务器上运行     |
| **npm**        | Node.js 的“应用商店 + 管理工具” |


## Node
- Node.js 是一个“能在电脑 / 服务器上运行 JavaScript 的环境”
- JavaScript  只能在浏览器里
- JavaScript  可以在本地、服务器、脚本、后端跑
- 由基金会治理

## npm
- npm = Node Package Manager
- npm 本身是一个用 JavaScript 写的程序，而它运行在 Node 上
- 由 GitHub（微软）运营

### npm 的作用
- npm 是前端世界的“应用商店 + 包管理工具”
- 下载别人写好的代码、管理依赖、跑项目命令
- 📦 管理依赖包
- ▶️ 运行项目脚本
- 🔁 统一版本 & 依赖关系

### 为什么 npm 和 Node 捆绑？
Node 和 npm 是两个不同的工具。

npm 强依赖 Node，所以官方把 npm 和 Node 捆绑发布、一起安装。
- Node 没有 npm → 生态用不了
- npm 没有 Node → 根本跑不了
- 技术上独立，发行时捆绑

类似
- Node.js = 操作系统内核（Linux）
- npm = 软件商店（App Store / apt）