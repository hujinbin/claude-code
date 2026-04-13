# Claude Code

[![TypeScript](https://img.shields.io/badge/TypeScript-5.0+-blue.svg)](https://www.typescriptlang.org/)
[![React](https://img.shields.io/badge/React-18+-61DAFB.svg)](https://react.dev/)
[![Bun](https://img.shields.io/badge/Bun-Runtime-orange.svg)](https://bun.sh/)

Claude Code 是 Anthropic 官方推出的 CLI 工具，提供交互式编程助手功能，通过自然语言对话帮助开发者完成软件工程任务。

**English Version**: [README_EN.md](./README_EN.md)

## 目录

- [概述](#概述)
- [架构设计](#架构设计)
- [功能特性](#功能特性)
- [安装](#安装)
- [使用方法](#使用方法)
- [开发](#开发)
- [项目结构](#项目结构)
- [命令参考](#命令参考)
- [技术栈](#技术栈)
- [参与贡献](#参与贡献)

## 概述

Claude Code 是一个基于 **React** 和 **Ink** 构建的终端应用程序，提供丰富的交互体验：

- 代码分析与导航
- 文件操作与编辑
- Shell 命令执行
- 任务管理与跟踪
- Git 操作集成
- 语音交互支持
- IDE 集成
- 以及更多功能

## 架构设计

### 技术栈

| 技术 | 说明 |
|------|------|
| [Bun](https://bun.sh/) | 快速的 JavaScript 运行时和打包工具 |
| [React](https://react.dev/) | UI 框架 |
| [Ink](https://github.com/vadimdemedes/ink) | 用于构建交互式命令行应用的 React 框架 |
| TypeScript | 类型安全的 JavaScript |
| React Hooks | 自定义状态管理 |

### 项目统计

- **源代码文件**: 998+ 个
- **TypeScript**: 1,332+ 个 `.ts` 文件
- **TSX 组件**: 552+ 个 `.tsx` 文件
- **CLI 命令**: 60+ 个
- **代理工具**: 40+ 个
- **React 组件**: 100+ 个

### 核心系统

#### 入口点 (`src/entrypoints/`)
- `cli.tsx` - 主 CLI 入口
- `init.ts` - 应用程序初始化
- `mcp.ts` - Model Context Protocol 入口

#### 命令系统 (`src/commands/`)
丰富的 CLI 命令，包括：
- **Git 操作**: `branch`, `commit`, `diff`, `review`
- **会话管理**: `resume`, `session`, `status`
- **配置管理**: `config`, `env`, `keybindings`, `theme`
- **工具命令**: `mcp`, `skills`, `tasks`, `voice`
- **实用工具**: `clear`, `help`, `version`, `doctor`
- **开发调试**: `debug-tool-call`, `perf-issue`, `sandbox-toggle`

#### 工具系统 (`src/tools/`)
40+ 个代理工具，涵盖：
- **文件操作**: `FileReadTool`, `FileWriteTool`, `FileEditTool`, `GlobTool`
- **搜索工具**: `GrepTool`, `WebSearchTool`, `ToolSearchTool`
- **命令执行**: `BashTool`, `PowerShellTool`, `REPLTool`
- **MCP 集成**: `MCPTool`, `McpAuthTool`, `ReadMcpResourceTool`
- **任务管理**: `TaskCreateTool`, `TaskListTool`, `TodoWriteTool`
- **通信工具**: `SendMessageTool`, `AskUserQuestionTool`
- **Notebook**: `NotebookEditTool`
- **实用工具**: `WebFetchTool`, `LSPTool`, `BriefTool`, `SleepTool`

#### 组件系统 (`src/components/`)
丰富的 React 组件库：
- **消息组件**: `Message`, `Messages`, `MessageRow`, `MessageResponse`
- **输入组件**: `TextInput`, `PromptInput`, `VimTextInput`
- **UI 元素**: `Spinner`, `SearchBox`, `StatusLine`
- **对话框**: `Settings`, `ExportDialog`, `MCPServerApprovalDialog`
- **反馈组件**: `Feedback`, `FeedbackSurvey`, `EffortIndicator`
- **权限对话框**: `permissions/` 目录
- **任务 UI**: `tasks/` 目录
- **技能 UI**: `skills/` 目录

#### 服务层 (`src/services/`)
后端服务架构：
- **API**: API 客户端和通信层
- **Analytics**: 使用分析和跟踪
- **MCP**: Model Context Protocol 实现
- **LSP**: Language Server Protocol 集成
- **OAuth**: 认证服务
- **Voice**: 语音识别和合成
- **Settings**: 配置同步
- **Memory**: 会话内存管理

#### 技能系统 (`src/skills/`)
可扩展的技能系统：
- `bundled/` - 内置技能（17 个文件）
- `mcpSkillBuilders.ts` - MCP 技能构建器

#### Vim 支持 (`src/vim/`)
完整的 Vim 快捷键支持：
- `motions.ts` - Vim 移动命令
- `operators.ts` - Vim 操作符
- `textObjects.ts` - 文本对象

#### 工具函数 (`src/utils/`)
500+ 个工具模块，涵盖：
- Git 操作
- 文件系统
- 配置管理
- 认证处理
- Markdown 处理
- 差异比较
- API 辅助函数
- 以及更多

## 功能特性

### 交互式助手
- 自然语言代码查询
- 上下文感知建议
- 多步骤任务执行
- 基于代理的自动化
- 团队协作支持

### 文件操作
- 带安全检查的文件读写编辑
- 基于模式的文件搜索（Glob）
- 内容搜索（Grep）
- 语法感知编辑
- Notebook 编辑（.ipynb 文件）

### 开发工具
- Bash/PowerShell 命令执行（带权限控制）
- Git 集成（状态、差异、提交、推送、PR）
- LSP 代码智能支持
- MCP（Model Context Protocol）集成
- 代码索引和分析

### 任务管理
- 任务创建与跟踪
- 待办事项管理
- 复杂实现的计划模式
- Worktree 隔离环境支持
- 会话历史和恢复
- 基于 Cron 的定时任务

### 语音交互
- 语音模式支持
- 语音转文本集成
- 语音命令处理

### IDE 集成
- 自动 IDE 检测和连接
- 支持 VSCode、JetBrains、Cursor
- 文件同步
- 深度链接

### 安全与控制
- 基于权限的工具执行
- Bash 命令沙箱模式
- 可配置的安全规则
- 破坏性操作的用户确认
- 隐私设置管理

## 安装

```bash
# 克隆仓库
git clone https://github.com/hujinbin/claude-code.git

# 进入项目目录
cd claude-code

# 安装依赖（需要 Bun）
bun install

# 构建项目
bun run build
```

### 环境要求

- [Bun](https://bun.sh/) 运行时
- Git

## 使用方法

```bash
# 启动 Claude Code
bun run start

# 或直接使用 CLI
bun run cli

# 查看帮助
claude --help
```

## 开发

```bash
# 开发模式运行（热重载）
bun run dev

# 构建项目
bun run build

# 运行测试
bun test

# 类型检查
bun run typecheck

# 代码检查
bun run lint

# 调试特定命令
bun run cli -- --help
```

## 项目结构

```
src/
├── assistant/           # 助手模式功能
├── bootstrap/           # 应用引导
├── bridge/              # 桥接通信（31 个文件）
├── buddy/               # Buddy 系统
├── cli/                 # CLI 工具（19 个文件）
├── commands/            # 命令实现（207 个文件）
│   ├── branch/          # Git 分支命令
│   ├── commit.ts        # Git 提交
│   ├── config/          # 配置命令
│   ├── help/            # 帮助系统
│   ├── login/           # 认证
│   ├── mcp/             # MCP 命令
│   ├── tasks/           # 任务命令
│   └── voice/           # 语音命令
├── components/          # React 组件（389 个文件）
│   ├── agents/          # 代理 UI 组件
│   ├── design-system/   # 设计系统
│   ├── messages/        # 消息组件
│   ├── permissions/     # 权限对话框
│   ├── PromptInput/     # 输入组件
│   ├── Settings/        # 设置 UI
│   └── tasks/           # 任务 UI
├── constants/           # 常量定义（21 个文件）
├── context/             # 上下文管理（9 个文件）
├── coordinator/         # 协调器模式
├── entrypoints/         # 应用入口点
│   ├── cli.tsx          # CLI 入口
│   ├── init.ts          # 初始化
│   └── mcp.ts           # MCP 入口
├── hooks/               # React Hooks（104 个文件）
├── ink/                 # 终端渲染（96 个文件）
├── keybindings/         # 快捷键定义（14 个文件）
├── main.tsx             # 核心应用编排
├── migrations/          # 数据迁移（11 个文件）
├── query.ts             # 查询处理
├── QueryEngine.ts       # 查询引擎
├── schemas/             # 数据模式
├── services/            # 后端服务（130 个文件）
│   ├── api/             # API 层（20 个文件）
│   ├── analytics/       # 分析（9 个文件）
│   ├── compact/         # 会话压缩（11 个文件）
│   ├── lsp/             # LSP 集成
│   ├── mcp/             # MCP 实现（23 个文件）
│   └── plugins/         # 插件系统
├── skills/              # 技能系统（20 个文件）
│   └── bundled/         # 内置技能（17 个文件）
├── tasks/               # 任务系统（12 个文件）
├── tools/               # 工具实现（184 个文件）
│   ├── AgentTool/       # 代理工具（20 个文件）
│   ├── BashTool/        # Bash 执行（18 个文件）
│   ├── PowerShellTool/  # PowerShell 执行（14 个文件）
│   └── ...
├── types/               # TypeScript 类型（11 个文件）
├── utils/               # 工具函数（564 个文件）
├── vim/                 # Vim 快捷键
│   ├── motions.ts       # Vim 移动命令
│   ├── operators.ts     # Vim 操作符
│   └── textObjects.ts   # 文本对象
└── voice/               # 语音功能
```

## 命令参考

### 核心命令
| 命令 | 描述 |
|------|------|
| `/branch` | Git 分支管理 |
| `/commit` | 创建 Git 提交 |
| `/diff` | 显示 Git 差异 |
| `/help` | 显示帮助信息 |
| `/clear` | 清屏 |
| `/exit` | 退出 Claude Code |

### 会话命令
| 命令 | 描述 |
|------|------|
| `/resume` | 恢复之前的会话 |
| `/status` | 显示会话状态 |
| `/session` | 会话管理 |
| `/history` | 查看对话历史 |

### 配置命令
| 命令 | 描述 |
|------|------|
| `/config` | 管理配置 |
| `/keybindings` | 配置快捷键 |
| `/theme` | 更改主题 |
| `/env` | 环境变量 |

### 开发命令
| 命令 | 描述 |
|------|------|
| `/doctor` | 诊断问题 |
| `/debug-tool-call` | 调试工具调用 |
| `/perf-issue` | 报告性能问题 |
| `/sandbox-toggle` | 切换沙箱模式 |

### 高级命令
| 命令 | 描述 |
|------|------|
| `/mcp` | MCP 服务器管理 |
| `/skills` | 技能管理 |
| `/tasks` | 任务管理 |
| `/voice` | 语音设置 |
| `/plan` | 计划模式 |
| `/worktree` | Worktree 管理 |

## 技术栈

- **Bun**: 快速的 JavaScript 运行时和打包工具
- **React**: UI 框架
- **Ink**: 用于构建交互式命令行应用的 React 框架
- **Commander.js**: CLI 框架
- **Chalk**: 终端样式
- **Zod**: 模式验证
- **TypeScript**: 类型安全的 JavaScript
- **Vitest**: 测试框架

## 参与贡献

这是 Anthropic 官方的 Claude Code 工具。贡献应符合项目目标和编码标准。

1. Fork 本仓库
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 创建 Pull Request

## 许可证

版权所有 © Anthropic PBC

本项目是 Anthropic 拥有的专有软件。

## 致谢

- 由 [Anthropic](https://anthropic.com) 构建
- 由 [Claude](https://claude.ai) 提供支持
- 终端 UI 由 [Ink](https://github.com/vadimdemedes/ink) 提供支持

## 技术支持

如需支持，请访问 [support.anthropic.com](https://support.anthropic.com) 或在 GitHub 上提交 issue。
