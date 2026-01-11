# Claude Canvas Plugin

TUI toolkit for Claude Code - spawn interactive terminal interfaces for calendars, weather, flight tracking, system monitoring, and more.

Based on [dvdsgl/claude-canvas](https://github.com/dvdsgl/claude-canvas) and [BEARLY-HODLING/claude-canvas](https://github.com/BEARLY-HODLING/claude-canvas).

## Prerequisites

- [Bun](https://bun.sh) runtime
- iTerm2 (macOS) or tmux for best experience

### Install Bun

**macOS/Linux:**
```bash
curl -fsSL https://bun.sh/install | bash
```

**Windows:**
```powershell
powershell -c "irm bun.sh/install.ps1 | iex"
```

## Installation

1. Add this marketplace in Claude Code:
   ```
   /plugin marketplace add riazmohamed/claude-canvas-plugin
   ```

2. Install the canvas plugin:
   ```
   /plugin install canvas
   ```

3. Run first-time setup (installs canvas dependencies):
   ```
   /canvas:setup
   ```

## Available Commands

| Command | Description |
|---------|-------------|
| `/canvas:setup` | One-time setup to install dependencies |
| `/canvas:calendar` | Weekly calendar view |
| `/canvas:weather` | Weather forecasts (Open-Meteo API) |
| `/canvas:tracker` | Live flight tracking (OpenSky Network) |
| `/canvas:system` | System resource monitor (CPU, memory, disk) |
| `/canvas:document [content]` | Markdown document viewer |
| `/canvas:meeting` | Meeting time picker |
| `/canvas:flight` | Flight booking interface |

## Canvas Controls

### Global (All Canvases)
| Key | Action |
|-----|--------|
| `?` | Help overlay |
| `Tab` | Canvas navigator |
| `q` | Exit canvas |

### Weather
| Key | Action |
|-----|--------|
| `/` | Search cities |
| `w`/`W` | Manage watchlist |
| Arrow keys | Navigate |

### Flight Tracker
| Key | Action |
|-----|--------|
| `s` | Search by callsign |
| `r` | Search by route |
| `Space` | Refresh |
| `+`/`-` | Adjust refresh rate |

### System Monitor
| Key | Action |
|-----|--------|
| `p` | Pause/resume |
| `+`/`-` | Adjust refresh |
| Arrows | Scroll processes |

### Calendar
| Key | Action |
|-----|--------|
| `←`/`→` | Navigate weeks |
| `t` | Jump to today |

## Platform Support

| Platform | Terminal | Support |
|----------|----------|---------|
| macOS | iTerm2 | Full (split panes) |
| macOS | tmux | Full (split panes) |
| macOS | Apple Terminal | Partial (new window) |
| macOS | VS Code Terminal | Partial (new window) |
| Windows | WSL2 + terminal | Full |
| Windows | Command Prompt | Limited |

## Troubleshooting

### Canvas doesn't spawn
- Verify terminal: `cd ~/tools/claude-canvas && bun run canvas/src/cli.ts env`
- For tmux: Start `tmux new-session -s dev` before Claude Code

### Command not found
- Run `/plugin` to verify installation
- Try `/plugin install canvas` again
- Restart Claude Code

### Bun not found
- Reload shell: `source ~/.zshrc` or `source ~/.bashrc`
- Verify: `bun --version`

## License

MIT

## Credits

- Original: [dvdsgl/claude-canvas](https://github.com/dvdsgl/claude-canvas)
- Enhanced fork: [BEARLY-HODLING/claude-canvas](https://github.com/BEARLY-HODLING/claude-canvas)
