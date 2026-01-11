# Claude Canvas Plugin

[![GitHub](https://img.shields.io/badge/GitHub-riazmohamed%2Fclaude--canvas--plugin-blue?logo=github)](https://github.com/riazmohamed/claude-canvas-plugin)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

> Give Claude Code its own display - spawn interactive TUI interfaces in split panes

**Repository:** [https://github.com/riazmohamed/claude-canvas-plugin](https://github.com/riazmohamed/claude-canvas-plugin)

A Claude Code plugin marketplace that brings [Claude Canvas](https://github.com/dvdsgl/claude-canvas) functionality to your workflow through simple slash commands. Spawn calendars, weather dashboards, flight trackers, system monitors, and more - all in a split pane next to your Claude Code session.

## What is Claude Canvas?

Claude Canvas is a TUI (Terminal User Interface) toolkit that extends Claude Code with an external display. Instead of just text responses, Claude can now spawn rich, interactive terminal interfaces that run alongside your coding session.

**Use cases:**
- View your calendar while scheduling meetings
- Monitor system resources while debugging performance issues
- Track flights while building travel apps
- Display markdown documents for reference

## Quick Start

### Step 1: Install Prerequisites

**Install Bun** (required runtime):

```bash
# macOS/Linux
curl -fsSL https://bun.sh/install | bash

# Windows (PowerShell)
powershell -c "irm bun.sh/install.ps1 | iex"
```

**Recommended terminal** (for split pane support):
- macOS: iTerm2 or tmux
- Windows: WSL2 with a proper terminal
- Linux: tmux

### Step 2: Install the Plugin

Clone this repository (or copy CLAUDE.md to your project):

```bash
git clone https://github.com/riazmohamed/claude-canvas-plugin.git
cd claude-canvas-plugin
```

Then open Claude Code in this directory and run one-time setup:

```
/canvas:setup
```

### Step 3: Start Using Canvas Commands

```bash
# Try it out!
/canvas:weather
/canvas:calendar
/canvas:system
```

## Available Commands

| Command | Description | Data Source |
|---------|-------------|-------------|
| `/canvas:setup` | One-time setup - installs dependencies | - |
| `/canvas:calendar` | Interactive weekly calendar view | Local |
| `/canvas:weather` | Weather conditions and 7-day forecast | Open-Meteo API (free) |
| `/canvas:tracker` | Live aircraft tracking with map | OpenSky Network (free) |
| `/canvas:system` | CPU, memory, disk, and process monitor | Local system |
| `/canvas:document [text]` | Markdown document viewer | User input |
| `/canvas:meeting` | Meeting time picker interface | Local |
| `/canvas:flight` | Flight booking UI with seat selection | Demo |

## Usage Examples

### Check the Weather
```bash
/canvas:weather
```
Then press `/` to search for a city, use arrow keys to navigate, and `w` to add to watchlist.

### Monitor System Resources
```bash
/canvas:system
```
View CPU sparklines, memory usage, disk space, and top processes in real-time.

### View a Calendar
```bash
/canvas:calendar
```
Use `←`/`→` to navigate weeks, `t` to jump to today.

### Display a Document
```bash
/canvas:document # My Notes

## Todo
- Review PR
- Update docs
```

## Keyboard Controls

### Global (All Canvases)
| Key | Action |
|-----|--------|
| `?` | Show help overlay |
| `Tab` | Canvas navigator |
| `q` | Exit/close canvas |

### Weather Canvas
| Key | Action |
|-----|--------|
| `/` | Search cities |
| `w` / `W` | Add/remove from watchlist |
| `Arrow keys` | Navigate locations |
| `Enter` | Select location |

### Flight Tracker
| Key | Action |
|-----|--------|
| `s` | Search by callsign |
| `r` | Search by route |
| `Space` | Manual refresh |
| `+` / `-` | Adjust refresh interval (5-60s) |

### System Monitor
| Key | Action |
|-----|--------|
| `p` | Pause/resume updates |
| `+` / `-` | Adjust refresh interval |
| `Arrow keys` | Scroll process list |

### Calendar
| Key | Action |
|-----|--------|
| `←` / `→` | Navigate weeks |
| `t` | Jump to today |
| `n` / `p` | Next/previous |

## Platform Support

| Platform | Terminal | Canvas Support |
|----------|----------|----------------|
| macOS | **iTerm2** | Full - native split panes |
| macOS | **tmux** | Full - split panes |
| macOS | Apple Terminal | Partial - opens new window |
| macOS | VS Code Terminal | Partial - opens new window |
| Linux | tmux | Full - split panes |
| Windows | **WSL2 + terminal** | Full - with proper terminal |
| Windows | Command Prompt | Limited - basic support |

**Best experience:** Use iTerm2 on macOS or tmux on any platform.

## How It Works

1. When you run `/canvas:setup`, the plugin clones the [BEARLY-HODLING/claude-canvas](https://github.com/BEARLY-HODLING/claude-canvas) toolkit to `~/tools/claude-canvas`
2. Each `/canvas:*` command spawns a Bun process that renders a TUI in a split pane
3. The canvas automatically detects your terminal and uses the appropriate method (iTerm2 AppleScript, tmux split, or new window)

## Troubleshooting

### Canvas doesn't appear or exits immediately

1. **Check terminal support:**
   ```bash
   cd ~/tools/claude-canvas && bun run canvas/src/cli.ts env
   ```

2. **Use tmux for guaranteed split pane support:**
   ```bash
   tmux new-session -s dev
   claude  # Start Claude Code inside tmux
   /canvas:weather
   ```

### "Command not found" error

1. Ensure you're in a directory with the CLAUDE.md file (or copy it to `~/.claude/CLAUDE.md` for global access)
2. Restart Claude Code
3. Verify CLAUDE.md contains the skill definitions

### "bun: command not found"

1. Reload your shell:
   ```bash
   source ~/.zshrc  # or ~/.bashrc
   ```
2. Verify installation:
   ```bash
   bun --version
   ```

### Setup failed or incomplete

Run setup again:
```bash
/canvas:setup
```

Or manually:
```bash
cd ~/tools/claude-canvas && git pull && bun install && cd canvas && bun install
```

## Uninstalling

```bash
# Remove the CLAUDE.md file (or delete the canvas skill definitions from it)
rm CLAUDE.md

# Optionally remove the canvas toolkit
rm -rf ~/tools/claude-canvas
```

## Contributing

Issues and PRs welcome! This plugin wraps the excellent [claude-canvas](https://github.com/dvdsgl/claude-canvas) project.

## License

MIT

## Credits

- Original Claude Canvas: [dvdsgl/claude-canvas](https://github.com/dvdsgl/claude-canvas)
- Enhanced fork with iTerm2/Terminal support: [BEARLY-HODLING/claude-canvas](https://github.com/BEARLY-HODLING/claude-canvas)
- Weather data: [Open-Meteo](https://open-meteo.com/) (free, no API key)
- Flight data: [OpenSky Network](https://opensky-network.org/) (free, no API key)
