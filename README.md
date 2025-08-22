# 🎵 Orchestra

**Professional Git worktree and tmux session management with AI automation.**

Orchestra is a high-performance, terminal-first system for orchestrating Git worktree and tmux session management with intelligent automation and a modern Rust-based TUI.

## ✨ Features

- **🚀 Native Performance** - Compiled Rust TUI with <100ms startup
- **🤖 AI-Powered Sessions** - Intelligent session naming with context detection
- **🌳 Hierarchical Navigation** - Tree view of worktrees with expandable sessions
- **⚡ Real-time Updates** - Live git status, session previews, auto-refresh
- **🎯 Cross-Repository** - Works from any git repository without configuration
- **🔄 Seamless Integration** - Full compatibility with existing Git and tmux workflows

## 🚀 Quick Start

### macOS (Intel)
```bash
curl -L https://github.com/adeperio/orchestra/releases/latest/download/gw-orchestrator-macos-intel.tar.gz | tar xz
cd gw-orchestrator-macos-intel && ./install.sh
```

### macOS (Apple Silicon)
```bash
curl -L https://github.com/adeperio/orchestra/releases/latest/download/gw-orchestrator-macos-arm64.tar.gz | tar xz
cd gw-orchestrator-macos-arm64 && ./install.sh
```

### Linux x64
```bash
curl -L https://github.com/adeperio/orchestra/releases/latest/download/gw-orchestrator-linux-x64.tar.gz | tar xz
cd gw-orchestrator-linux-x64 && ./install.sh
```

## 🎮 Usage

```bash
# Launch the primary TUI interface (recommended)
gwr

# Or use the CLI interface  
gw ls          # List worktrees
gw ch main     # Switch to main branch
gw d old-feature  # Delete worktree and branch
```

### TUI Interface (gwr)

The main interface provides:
- **Visual Navigation**: Hierarchical tree view of worktrees and sessions
- **AI Session Management**: Auto-rename sessions with context detection
- **Real-time Updates**: Live git status and session previews
- **One-key Operations**: Create, delete, switch with single keystrokes

**Key Controls:**
- `↑/↓` Navigate • `Enter` Select/Expand • `d` Delete • `c` Create • `q` Quit

## 🔧 Shell Integration

For directory switching, add to your `~/.bashrc` or `~/.zshrc`:

```bash
gwr() {
  local out="$(command gwr "$@")"
  local status=$?
  local cd_line="$(echo "$out" | grep -m1 '^cd')"
  [[ -n $cd_line ]] && eval "$cd_line"
  echo "$out" | grep -v '^cd'
  return $status
}

gw() {
  local out="$(command gw "$@")"  
  local status=$?
  local cd_line="$(echo "$out" | grep -m1 '^cd')"
  [[ -n $cd_line ]] && eval "$cd_line"
  echo "$out" | grep -v '^cd'
  return $status
}
```

## 🤖 AI Features

For AI-powered session naming, set your API key:

```bash
export ANTHROPIC_API_KEY="your-api-key"
```

Sessions with `auto_` prefix automatically rename based on:
- Terminal output analysis
- Current command detection  
- Application context (OpenCode, SSH, Docker, etc.)

## 📦 Installation Options

### Manual Download
1. Download the appropriate package from [Releases](https://github.com/adeperio/orchestra/releases)
2. Extract: `tar xzf gw-orchestrator-*.tar.gz`
3. Run: `./install.sh`

### Package Contents
Each release package includes:
- Pre-compiled binary (`gw-orchestrator`)
- Runtime shell scripts (`gwr.sh`, `gw.sh`, APIs)
- Installation script with proper permissions
- Platform-specific optimizations

## 🔧 Requirements

- **Git 2.5+** (for `git worktree` support)
- **tmux** (for session management)
- **bash** (shell integration)
- **jq** (JSON processing)

## 🏗️ Architecture

Orchestra uses a **bridge architecture**:
- **Rust TUI** - High-performance native interface
- **Shell APIs** - Battle-tested Git and tmux operations
- **Bridge Communication** - JSON-based API layer
- **Cross-Platform** - Single binary per platform

## 🚀 Workflow

1. **Launch TUI** (`gwr`) from any git repository
2. **Navigate visually** through worktrees and sessions
3. **Create sessions** - Automatically marked for AI naming
4. **Work & detach** - Normal tmux workflow (Ctrl+B, D)
5. **Return to TUI** - Sessions intelligently renamed with context
6. **Persistent state** - UI remembers selections and expansions

## 🤝 Support

For issues and feature requests, please create an issue in this repository.

---

**Built with ❤️ using Rust + ratatui for modern terminal experiences.**

Professional development workflow orchestration for teams and individuals.
