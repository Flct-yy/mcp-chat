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




# AI Chat Application

A minimalist chat application with OpenAI API integration and file upload support.

## Features

- 🤖 OpenAI API integration (GPT-4 compatible)
- 📎 File upload support (PDF, Word, Excel, Images)
- 🎨 Minimalist design with dark/light themes
- ⚡ Built with Vite + React + TypeScript
- 🎯 Tailwind CSS 4 for styling
- 🔐 Session management
- 💾 Local conversation storage

## Quick Start

### Prerequisites

- Node.js 18+ 
- npm or pnpm
- OpenAI API key (optional for development)

### Installation

```bash
# Clone the repository
git clone <your-repo-url>
cd boilerplate-vite-ts-tailwindcss-shadcn

# Install dependencies
npm install

# Create environment file
cp .env.example .env

# Add your OpenAI API key to .env
# VITE_OPENAI_API_KEY=your-api-key-here
```

### Development

```bash
# Start development server
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview
```

## Configuration

### Environment Variables

Create a `.env` file in the root directory:

```env
# API Configuration
VITE_API_BASE_URL=http://localhost:3000  # Your backend URL
VITE_OPENAI_API_KEY=sk-...              # OpenAI API key
VITE_OPENAI_MODEL=gpt-4                 # Model to use
```

### Using with OpenAI API

1. **Direct OpenAI Connection:**
   ```env
   VITE_API_BASE_URL=https://api.openai.com
   VITE_OPENAI_API_KEY=sk-your-key-here
   ```

2. **Using a Backend Proxy:**
   ```env
   VITE_API_BASE_URL=http://localhost:3000
   # API key handled by backend
   ```

## API Endpoints

The application expects the following endpoints (OpenAI-compatible):

- `POST /v1/chat/completions` - Chat completions
- `POST /v1/files` - File upload
- `GET /v1/files` - List files
- `DELETE /v1/files/:id` - Delete file
- `GET /v1/sessions` - List sessions
- `DELETE /v1/sessions/:id` - Delete session

## File Upload

Supported file types:
- Documents: PDF, Word (.doc, .docx), Text (.txt)
- Spreadsheets: Excel (.xlsx, .xls), CSV
- Images: PNG, JPG, JPEG
- Data: JSON, Markdown

Max file size: 10MB per file

## Tech Stack

- **Frontend:** React 18, TypeScript
- **Build:** Vite 5
- **Styling:** Tailwind CSS 4, shadcn/ui
- **State:** React Context API
- **Storage:** LocalStorage
- **API:** OpenAI-compatible REST API

## Project Structure

```
src/
├── components/       # React components
│   ├── ui/          # shadcn/ui components
│   ├── chat/        # Chat-specific components
│   └── auth/        # Authentication components
├── contexts/        # React contexts
├── services/        # API services
├── config/          # Configuration files
├── hooks/           # Custom React hooks
├── lib/            # Utility functions
├── pages/          # Page components
└── types/          # TypeScript types
```

## License

MIT