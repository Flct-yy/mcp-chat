基于 MCP（Model Context Protocol）的设计思想，实现了一个前端 AI Agent Chat Demo。
在该项目中，前端不仅负责 UI 渲染，还承担了 MCP Client 的职责，统一管理 Agent 的决策流程、Tool 调用和结果渲染。
Agent 会根据用户输入判断是否需要调用工具，工具以 schema 的形式注册，前端通过统一接口执行并将结果反馈给聊天系统。

## 🔹 1️⃣ MCP Client（前端核心）
- 在前端实现 MCP Client
- 抽象 Tool 注册、调用、返回结构
- Agent 逻辑与 UI 解耦

## 🔹 2️⃣ Agent 决策流程
- 用户输入 → Agent 判断
- 是否调用 Tool
- Tool 执行 → 结果返回 → 回复生成

## 🔹 3️⃣ Tool Schema 驱动
- 每个 Tool 通过 schema 注册
- 前端可动态扩展工具
- Tool 输出统一结构，方便 UI 渲染

## 🔹 4️⃣ Chat UI + Agent 状态
- Chat UI 只关心消息渲染
- Agent / Tool 作为独立模块
- 支持后续扩展为多 Agent




# AI 聊天应用

一个集成 OpenAI API 并支持文件上传的极简聊天应用。

## 功能特点

- 🤖 集成 OpenAI API（兼容 GPT-4）
- 📎 支持文件上传（PDF、Word、Excel、图片）
- 🎨 极简设计，支持深色/浅色主题
- ⚡ 使用 Vite + React + TypeScript 构建
- 🎯 使用 Tailwind CSS 4 进行样式设计
- 🔐 会话管理
- 💾 本地对话存储

## 快速开始

### 前置要求

- Node.js 18+ 
- npm 或 pnpm
- OpenAI API 密钥（开发时可选）

### 安装

```bash
# 克隆仓库
git clone <your-repo-url>
cd boilerplate-vite-ts-tailwindcss-shadcn

# 安装依赖
npm install

# 创建环境文件
cp .env.example .env

# 在 .env 中添加你的 OpenAI API 密钥
# VITE_OPENAI_API_KEY=your-api-key-here
```

### 开发

```bash
# 启动开发服务器
npm run dev

# 构建生产版本
npm run build

# 预览生产构建
npm run preview
```

## 配置

### 环境变量

在根目录创建 `.env` 文件：

```env
# API 配置
VITE_API_BASE_URL=http://localhost:3000  # 你的后端 URL
VITE_OPENAI_API_KEY=sk-...              # OpenAI API 密钥
VITE_OPENAI_MODEL=gpt-4                 # 使用的模型
```

### 使用 OpenAI API

1. **直接连接 OpenAI：**
   ```env
   VITE_API_BASE_URL=https://api.openai.com
   VITE_OPENAI_API_KEY=sk-your-key-here
   ```

2. **使用后端代理：**
   ```env
   VITE_API_BASE_URL=http://localhost:3000
   # API 密钥由后端处理
   ```

## API 端点

应用期望以下端点（兼容 OpenAI）：

- `POST /v1/chat/completions` - 聊天完成
- `POST /v1/files` - 文件上传
- `GET /v1/files` - 列出文件
- `DELETE /v1/files/:id` - 删除文件
- `GET /v1/sessions` - 列出会话
- `DELETE /v1/sessions/:id` - 删除会话

## 文件上传

支持的文件类型：
- 文档：PDF、Word (.doc, .docx)、文本 (.txt)
- 电子表格：Excel (.xlsx, .xls)、CSV
- 图片：PNG、JPG、JPEG
- 数据：JSON、Markdown

每个文件最大大小：10MB

## 技术栈

- **前端：** React 18、TypeScript
- **构建：** Vite 5
- **样式：** Tailwind CSS 4、shadcn/ui
- **状态管理：** React Context API
- **存储：** LocalStorage
- **API：** 兼容 OpenAI 的 REST API

## 项目结构


```
src/
├── components/       # React 组件
│   ├── ui/          # shadcn/ui 组件
│   ├── chat/        # 聊天相关组件
│   ├── auth/        # 认证组件
│   └── mcp/         # MCP 相关组件
├── contexts/        # React 上下文
├── mcp/             # MCP Client 核心实现
│   ├── client/      # MCP Client 逻辑
│   ├── agent/       # Agent 决策流程
│   └── tools/       # 工具定义与实现
├── services/        # API 服务
├── config/          # 配置文件
├── hooks/           # 自定义 React hooks
├── lib/             # 工具函数
├── pages/           # 页面组件
└── types/           # TypeScript 类型定义
```

## License

MIT