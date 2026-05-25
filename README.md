# Claude Code Project

第一次版本上传 — 2026/05/25

## 项目概况

本仓库是基于 Claude Code 构建的项目，涵盖以下内容：

- **Hyperframes 动画/视频项目**：使用 HTML/CSS/JS 制作动态视频内容
- **16 个 Agent Skills**：包括 animejs、gsap、tailwind、three.js、waapi、lottie 等前端动画技能
- **Claude Code 配置**：权限设置、MCP 工具（Playwright 浏览器自动化）

## 操作日志

### 第一阶段：环境搭建与技能发现

| 操作 | 掌握内容 |
|------|----------|
| 了解 Claude Code 的基本使用方式 | 通过 prompt 指挥 agent 进行代码编写 |
| 安装 `find-skills` 技能 | 学会用 `npx skills add` 安装技能到项目 |
| 搜索 Excel 相关技能 | 了解 Skills CLI 生态系统和技能市场 |

### 第二阶段：Excel 技能安装

| 操作 | 掌握内容 |
|------|----------|
| 对比文件级 vs MCP 级 Excel 技能 | 理解两种技能类型：`xlsx`（文件读写）vs `excel-mcp`（COM 实时操控） |
| 安装 `anthropics/skills@xlsx`（90K 安装量） | 全局安装命令 `npx skills add -g -y` |
| 安装 `sbroenne/mcp-server-excel@excel-mcp`（1.1K 安装量） | MCP 服务器需配合 Microsoft Excel 2016+ 使用 |

### 第三阶段：Git & GitHub

| 操作 | 掌握内容 |
|------|----------|
| 生成 ED25519 SSH 密钥 | `ssh-keygen -t ed25519` |
| 添加公钥到 GitHub | GitHub Settings → SSH Keys → 粘贴公钥 |
| 解决 "Host key verification failed" | `ssh-keyscan` 或 `StrictHostKeyChecking=no` |
| 解决 "Permission denied (publickey)" | SSH 密钥格式必须是完整的 OpenSSH 公钥格式 |
| `git init` 初始化仓库 | 将本地项目纳入版本控制 |
| 编写 `.gitignore` | 排除 `.thumbnails/`、`.playwright-mcp/` 等非必要文件 |
| `git remote add` + `git push` | 关联远程仓库并推送（SSH 协议） |

### 第四阶段：网络问题排查

| 遇到的问题 | 原因与解决 |
|------------|-----------|
| GitHub HTTPS 443 端口不通 | 国内网络限制，改用 SSH（端口 22） |
| npm 能通但 git 不通 | npm 配置了国内镜像 `registry.npmmirror.com` |
| SSH host key 验证失败 | 首次连接需将 GitHub 加入 `known_hosts` |

## 学习进度分析

### 已掌握
- Claude Code agent 的基本交互模式
- Skills 生态系统：搜索、安装、全局/项目级区别
- 文件级工具（xlsx）与 MCP 服务器工具（excel-mcp）的架构区别
- Git 基础：init、add、commit、remote、push
- SSH 密钥认证原理与 GitHub 配置
- 网络问题排查思路（HTTPS vs SSH、镜像代理）

### 进行中
- GitHub 工作流（commit 规范、分支管理、PR）
- MCP 服务器配置与使用（excel-mcp 还需配置 `.mcp.json`）

### 下一步
- 配置 `excel-mcp` 的 MCP 服务器连接
- 学习使用 `xlsx` 技能进行实际的 Excel 文件操作
- 建立规范的 commit 习惯和分支管理

---

*此 README 记录截至首次上传的完整操作历程。*
