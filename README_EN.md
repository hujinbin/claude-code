# Claude Code

Claude Code is Anthropic's official CLI tool for Claude, providing an interactive coding assistant that helps with software engineering tasks through natural language conversations.

## Overview

Claude Code is a terminal-based application built with **React** and **Ink**, offering a rich interactive experience for:

- Code analysis and navigation
- File operations and editing
- Shell command execution
- Task management and tracking
- Git operations integration
- Voice interaction support
- IDE integration
- And much more

## Architecture

### Technology Stack

- **Runtime**: [Bun](https://bun.sh/) - Fast JavaScript runtime and bundler
- **UI Framework**: React + [Ink](https://github.com/vadimdemedes/ink) (React for interactive CLIs)
- **Language**: TypeScript
- **State Management**: Custom state management with React hooks

### Project Statistics

- **Total Files**: 998+ source files
- **TypeScript**: 1,332+ `.ts` files
- **TSX**: 552+ `.tsx` files
- **Commands**: 60+ CLI commands
- **Tools**: 40+ agent tools
- **Components**: 100+ React components

### Core Systems

#### Entry Points (`src/entrypoints/`)
- `cli.tsx` - Main CLI entry point
- `init.ts` - Application initialization
- `mcp.ts` - Model Context Protocol entry

#### Commands (`src/commands/`)
Comprehensive CLI commands including:
- **Git Operations**: `branch`, `commit`, `diff`, `review`
- **Session Management**: `resume`, `session`, `status`
- **Configuration**: `config`, `env`, `keybindings`, `theme`
- **Tools**: `mcp`, `skills`, `tasks`, `voice`
- **Utilities**: `clear`, `help`, `version`, `doctor`
- **Development**: `debug-tool-call`, `perf-issue`, `sandbox-toggle`

#### Tools (`src/tools/`)
40+ Agent tools for various operations:
- **File Operations**: `FileReadTool`, `FileWriteTool`, `FileEditTool`, `GlobTool`
- **Search**: `GrepTool`, `WebSearchTool`, `ToolSearchTool`
- **Execution**: `BashTool`, `PowerShellTool`, `REPLTool`
- **MCP**: `MCPTool`, `McpAuthTool`, `ReadMcpResourceTool`
- **Task Management**: `TaskCreateTool`, `TaskListTool`, `TodoWriteTool`
- **Communication**: `SendMessageTool`, `AskUserQuestionTool`
- **Notebook**: `NotebookEditTool`
- **Utilities**: `WebFetchTool`, `LSPTool`, `BriefTool`, `SleepTool`

#### Components (`src/components/`)
Rich React component library:
- **Messages**: `Message`, `Messages`, `MessageRow`, `MessageResponse`
- **Input**: `TextInput`, `PromptInput`, `VimTextInput`
- **UI Elements**: `Spinner`, `SearchBox`, `StatusLine`
- **Dialogs**: `Settings`, `ExportDialog`, `MCPServerApprovalDialog`
- **Feedback**: `Feedback`, `FeedbackSurvey`, `EffortIndicator`
- **Permissions**: `permissions/` - Permission request dialogs
- **Tasks**: `tasks/` - Task management UI
- **Skills**: `skills/` - Skill system UI

#### Services (`src/services/`)
Backend services architecture:
- **API**: API client and communication layer
- **Analytics**: Usage analytics and tracking
- **MCP**: Model Context Protocol implementation
- **LSP**: Language Server Protocol integration
- **OAuth**: Authentication services
- **Voice**: Voice recognition and synthesis
- **Settings**: Configuration synchronization
- **Memory**: Session memory management

#### Skills System (`src/skills/`)
Extensible skill system for custom capabilities:
- `bundled/` - Built-in skills
- `mcpSkillBuilders.ts` - MCP skill builders

#### Vim Support (`src/vim/`)
Full Vim keybinding support:
- `motions.ts` - Vim motions
- `operators.ts` - Vim operators
- `textObjects.ts` - Text objects

#### Utilities (`src/utils/`)
500+ utility modules covering:
- Git operations
- File system
- Configuration
- Authentication
- Markdown processing
- Diff utilities
- API helpers
- And more

## Features

### Interactive Assistance
- Natural language code queries
- Context-aware suggestions
- Multi-step task execution
- Agent-based automation
- Teammate collaboration support

### File Operations
- Read/write/edit files with safety checks
- Pattern-based file search (Glob)
- Content search (Grep)
- Syntax-aware editing
- Notebook editing (.ipynb files)

### Development Tools
- Bash/PowerShell command execution with permission controls
- Git integration (status, diff, commit, push, PR)
- LSP support for code intelligence
- MCP (Model Context Protocol) integration
- Code indexing and analysis

### Task Management
- Task creation and tracking
- Todo list management
- Plan mode for complex implementations
- Worktree support for isolated environments
- Session history and resumption
- Cron-based scheduled tasks

### Voice Interaction
- Voice mode support
- Speech-to-text integration
- Voice command processing

### IDE Integration
- Automatic IDE detection and connection
- VSCode, JetBrains, and Cursor support
- File synchronization
- Deep linking

### Safety & Control
- Permission-based tool execution
- Sandbox mode for bash commands
- Configurable safety rules
- User confirmation for destructive actions
- Privacy settings management

## Installation

```bash
# Clone the repository
git clone https://github.com/hujinbin/claude-code.git

# Navigate to the project directory
cd claude-code

# Install dependencies (requires Bun)
bun install

# Build the project
bun run build
```

### Prerequisites

- [Bun](https://bun.sh/) runtime
- Git

## Usage

```bash
# Start Claude Code
bun run start

# Or use the CLI directly
bun run cli

# With specific options
claude --help
```

## Development

```bash
# Run in development mode with hot reload
bun run dev

# Build the project
bun run build

# Run tests
bun test

# Type check
bun run typecheck

# Lint
bun run lint

# Run specific commands for debugging
bun run cli -- --help
```

## Project Structure

```
src/
├── assistant/           # Assistant mode functionality
├── bootstrap/           # Application bootstrap
├── bridge/              # Bridge communication (31 files)
├── buddy/               # Buddy system
├── cli/                 # CLI utilities (19 files)
├── commands/            # Command implementations (207 files)
│   ├── branch/          # Git branch commands
│   ├── commit.ts        # Git commit
│   ├── config/          # Configuration commands
│   ├── help/            # Help system
│   ├── login/           # Authentication
│   ├── mcp/             # MCP commands
│   ├── tasks/           # Task commands
│   └── voice/           # Voice commands
├── components/          # React components (389 files)
│   ├── agents/          # Agent UI components
│   ├── design-system/   # Design system
│   ├── messages/        # Message components
│   ├── permissions/     # Permission dialogs
│   ├── PromptInput/     # Input components
│   ├── Settings/        # Settings UI
│   └── tasks/           # Task UI
├── constants/           # Constants (21 files)
├── context/             # Context management (9 files)
├── coordinator/         # Coordinator mode
├── entrypoints/         # Application entry points
│   ├── cli.tsx          # CLI entry
│   ├── init.ts          # Initialization
│   └── mcp.ts           # MCP entry
├── hooks/               # React hooks (104 files)
├── ink/                 # Terminal rendering (96 files)
├── keybindings/         # Keybinding definitions (14 files)
├── main.tsx             # Core application orchestration
├── migrations/          # Data migrations (11 files)
├── query.ts             # Query handling
├── QueryEngine.ts       # Query engine
├── schemas/             # Data schemas
├── services/            # Backend services (130 files)
│   ├── api/             # API layer (20 files)
│   ├── analytics/       # Analytics (9 files)
│   ├── compact/         # Session compaction (11 files)
│   ├── lsp/             # LSP integration
│   ├── mcp/             # MCP implementation (23 files)
│   └── plugins/         # Plugin system
├── skills/              # Skill system (20 files)
│   └── bundled/         # Built-in skills (17 files)
├── tasks/               # Task system (12 files)
├── tools/               # Tool implementations (184 files)
│   ├── AgentTool/       # Agent tools (20 files)
│   ├── BashTool/        # Bash execution (18 files)
│   ├── PowerShellTool/  # PowerShell execution (14 files)
│   └── ...
├── types/               # TypeScript types (11 files)
├── utils/               # Utility functions (564 files)
├── vim/                 # Vim keybindings
│   ├── motions.ts
│   ├── operators.ts
│   └── textObjects.ts
└── voice/               # Voice functionality
```

## Key Technologies & Dependencies

- **Bun**: Fast JavaScript runtime and bundler
- **React**: UI framework
- **Ink**: React for interactive command-line apps
- **Commander.js**: CLI framework
- **Chalk**: Terminal styling
- **Zod**: Schema validation
- **TypeScript**: Type-safe JavaScript
- **Vitest**: Testing framework

## Commands Reference

### Core Commands
| Command | Description |
|---------|-------------|
| `/branch` | Git branch management |
| `/commit` | Create git commits |
| `/diff` | Show git diffs |
| `/help` | Show help information |
| `/clear` | Clear the screen |
| `/exit` | Exit Claude Code |

### Session Commands
| Command | Description |
|---------|-------------|
| `/resume` | Resume previous session |
| `/status` | Show session status |
| `/session` | Session management |
| `/history` | View conversation history |

### Configuration Commands
| Command | Description |
|---------|-------------|
| `/config` | Manage configuration |
| `/keybindings` | Configure keybindings |
| `/theme` | Change color theme |
| `/env` | Environment variables |

### Development Commands
| Command | Description |
|---------|-------------|
| `/doctor` | Diagnose issues |
| `/debug-tool-call` | Debug tool calls |
| `/perf-issue` | Report performance issues |
| `/sandbox-toggle` | Toggle sandbox mode |

### Advanced Commands
| Command | Description |
|---------|-------------|
| `/mcp` | MCP server management |
| `/skills` | Skill management |
| `/tasks` | Task management |
| `/voice` | Voice settings |
| `/plan` | Plan mode |
| `/worktree` | Worktree management |

## Contributing

This is Anthropic's official Claude Code tool. Contributions should align with the project's goals and coding standards.

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

Copyright © Anthropic PBC

This project is proprietary software owned by Anthropic.

## Acknowledgments

- Built by [Anthropic](https://anthropic.com)
- Powered by [Claude](https://claude.ai)
- Terminal UI powered by [Ink](https://github.com/vadimdemedes/ink)

## Support

For support, visit [support.anthropic.com](https://support.anthropic.com) or open an issue on GitHub.
