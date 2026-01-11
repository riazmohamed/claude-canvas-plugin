# Claude Canvas Plugin

This project provides TUI canvas commands for Claude Code.

## Skills

### /canvas:setup
One-time setup to install Claude Canvas dependencies.

Run these commands in sequence:
1. `mkdir -p ~/tools && cd ~/tools && git clone https://github.com/BEARLY-HODLING/claude-canvas.git 2>/dev/null || (cd claude-canvas && git pull)`
2. `cd ~/tools/claude-canvas && bun install && cd canvas && bun install`
3. `cd ~/tools/claude-canvas && bun run canvas/src/cli.ts env`

### /canvas:weather
Spawn a weather canvas with forecasts.
Run: `cd ~/tools/claude-canvas && bun run canvas/src/cli.ts spawn weather`

### /canvas:calendar
Spawn an interactive calendar canvas in a split pane.
Run: `cd ~/tools/claude-canvas && bun run canvas/src/cli.ts spawn calendar`

### /canvas:system
Spawn system resource monitoring canvas.
Run: `cd ~/tools/claude-canvas && bun run canvas/src/cli.ts spawn system`

### /canvas:document [content]
Spawn a markdown document canvas. Pass content as argument.
Run: `cd ~/tools/claude-canvas && bun run canvas/src/cli.ts spawn document --config '{"content":"$ARGUMENTS"}'`

### /canvas:meeting
Spawn calendar in meeting picker mode for scheduling.
Run: `cd ~/tools/claude-canvas && bun run canvas/src/cli.ts spawn calendar --scenario meeting-picker`

### /canvas:tracker
Spawn live flight tracking canvas.
Run: `cd ~/tools/claude-canvas && bun run canvas/src/cli.ts spawn tracker`

### /canvas:flight
Spawn flight booking interface with seat selection.
Run: `cd ~/tools/claude-canvas && bun run canvas/src/cli.ts spawn flight`
