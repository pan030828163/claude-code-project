# 什么是 MCP？

> 本文整理自阿里云官方文章和知乎专栏，帮助快速理解 MCP（Model Context Protocol）的核心概念。

## 一、基本概念

**MCP** 全称 **Model Context Protocol（模型上下文协议）**，是由 Anthropic（Claude 的母公司）于 2024 年 11 月底推出的一种**开放标准协议**。

简单来说，MCP 是 AI 领域的 **"USB 接口"**——它在 AI 大模型与外部数据源（文件、数据库、API、开发工具等）之间建立标准化的双向安全连接，用统一的协议取代碎片化的集成方式。

> 如果把 LLM 比作人的大脑，MCP 就是手脚。LLM 不断提升智能下限，MCP 不断提升创意上限。

## 二、为什么需要 MCP？

在 MCP 出现之前，大模型接入外部数据的方式存在诸多痛点：

| 方式 | 局限 |
|------|------|
| 调用 API 接口 | 每个数据源需要单独对接 |
| 编写特定连接代码 | 重复造轮子，维护成本高 |
| LangChain / LlamaIndex 等框架 | 代码抽象度高，商业化过重 |
| 插件系统 | 封闭生态，通用性差 |

MCP 的核心价值：

- **标准化与通用性**：统一协议规范，跨系统无缝兼容
- **开发效率**：无需为每个数据源编写专门接口代码
- **双向通信**：AI 与数据源之间形成交互闭环
- **安全机制**：内置访问控制、权限设置和审计跟踪

## 三、核心架构

MCP 采用**客户端-服务器（Client-Server）架构**：

```
┌─────────────────────────────────────────────┐
│                  MCP Host                     │
│  (Claude Desktop / Cursor / IDE / AI 工具)    │
│         ┌──────────────────┐                  │
│         │   MCP Client     │ (1:1 连接)       │
│         └────────┬─────────┘                  │
└──────────────────┼────────────────────────────┘
                   │
    ┌──────────────┼──────────────┐
    │              │              │
┌───▼───┐    ┌────▼────┐    ┌───▼───┐
│ MCP   │    │ MCP     │    │ MCP   │
│Server │    │ Server  │    │Server │
│(本地) │    │ (远程)  │    │(社区) │
└───┬───┘    └────┬────┘    └───┬───┘
    │              │              │
┌───▼───┐    ┌────▼────┐    ┌───▼───┐
│本地文  │    │ 外部 API │    │第三方  │
│件/数据 │    │ (Slack,  │    │服务    │
│库      │    │ GitHub)  │    │        │
└───────┘    └─────────┘    └───────┘
```

### 主要组件

| 组件 | 角色 |
|------|------|
| **MCP Host** | 发起请求的 LLM 应用程序（如 Claude Desktop、Cursor） |
| **MCP Client** | 在 Host 内部与 MCP Server 保持 1:1 连接 |
| **MCP Server** | 提供上下文、工具（Tools）和提示（Prompts） |
| **Local Resources** | 本地文件、数据库等 |
| **Remote Resources** | 通过 API 访问的外部服务 |

### MCP Server 提供 3 种能力

1. **资源（Resources）**：类似文件的数据，可被客户端读取
2. **工具（Tools）**：可被 LLM 调用的函数（需用户批准）
3. **提示（Prompts）**：预编写的模板，帮助用户完成特定任务

## 四、工作原理

一次完整的 MCP 调用包含 6 个步骤：

```
用户提问 → AI Agent(MCP Client) → LLM 推理 → 选择 MCP Server/Tool
    ↑                                                        │
    │                                                        ▼
    返回结果 ← LLM 整理 ← 返回工具结果 ← 调用 MCP Tool
```

1. **用户提问**：用户向 AI Agent 提问（如"现在几点了？"）
2. **LLM 推理**：MCP Client 把问题 + 可用 Server/Tool 信息发给 LLM
3. **选择工具**：LLM 决定使用哪个 MCP Server 的哪个 Tool
4. **执行调用**：MCP Client 调用对应的 MCP Tool 获取结果
5. **结果回传**：将工具执行结果返回给 LLM
6. **生成回答**：LLM 整理后返回给用户

> 关键点：MCP Server 和 Tool 的描述信息本质上是 **System Prompt / 提示工程**，它让 LLM 知道有什么能力可用、何时该用。

## 五、通信机制

MCP 支持两种通信方式：

| 方式 | 协议 | 适用场景 |
|------|------|----------|
| **本地通信** | stdio | 同一台机器上的 Client 和 Server |
| **远程通信** | SSE (Server-Sent Events) + HTTP | 跨网络、分布式部署 |

两种方式均使用 **JSON-RPC 2.0** 格式进行消息传输。

## 六、MCP vs Function Calling

| 对比项 | MCP | Function Calling |
|--------|-----|------------------|
| 本质 | 开放标准协议 | 模型调用函数的机制 |
| 范围 | 连接外部数据源和工具 | AI 模型调用预定义函数 |
| 开放性 | 开放标准，跨平台通用 | 平台绑定 |
| 生态 | 社区驱动，可复用 | 需自行开发 |

## 七、实际应用

### 支持的客户端

| 客户端 | 资源 | 提示 | 工具 |
|--------|:----:|:----:|:----:|
| Claude Desktop | ✅ | ✅ | ✅ |
| Cursor | ❌ | ❌ | ✅ |
| Zed | ❌ | ✅ | ❌ |
| Continue | ✅ | ✅ | ✅ |

### 常用 MCP Server 示例

**数据与文件系统：**
- 文件系统（安全文件操作）
- PostgreSQL / SQLite（数据库访问）
- Google Drive（文件搜索）

**开发工具：**
- Git（仓库操作）
- GitHub / GitLab（项目管理）
- Sentry（错误分析）

**网络与浏览器：**
- Brave Search（网络搜索）
- Puppeteer（浏览器自动化）
- Fetch（网页内容获取）

**生产力工具：**
- Slack（消息管理）
- Google Maps（位置服务）
- Memory（持久记忆系统）

## 八、快速上手

### Claude Desktop 配置

1. 安装 Claude Desktop
2. 进入 Settings → Developer → Edit Config
3. 在 `claude_desktop_config.json` 中添加：

```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "/path/to/allowed/files"]
    },
    "git": {
      "command": "uvx",
      "args": ["mcp-server-git", "--repository", "path/to/git/repo"]
    }
  }
}
```

### Cursor 配置

文件 → 首选项 → Cursor Settings → Features → MCP Server → Add new MCP Server

## 九、生态资源

**官方资源：**
- 官方文档：https://modelcontextprotocol.io
- 官方 GitHub：https://github.com/modelcontextprotocol
- 官方 Server 列表：https://github.com/modelcontextprotocol/servers
- Anthropic 博客：https://www.anthropic.com/news/model-context-protocol

**社区资源：**
- Cursor Directory：https://cursor.directory/
- Pulsemcp：https://www.pulsemcp.com/
- Glama MCP Servers：https://glama.ai/mcp/servers

---

## 参考资料

1. [阿里云 - 什么是MCP？](https://www.aliyun.com/getting-started/what-is/what-is-mcp)
2. [知乎 - 一文看懂：MCP(大模型上下文协议)](https://zhuanlan.zhihu.com/p/27327515233)
