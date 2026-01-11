---
allowed-tools: Bash(mkdir:*), Bash(git:*), Bash(bun:*), Bash(cd:*)
description: One-time setup to install Claude Canvas dependencies
---
Set up Claude Canvas by running these commands:

1. Create tools directory and clone canvas:
!`mkdir -p ~/tools && cd ~/tools && git clone https://github.com/BEARLY-HODLING/claude-canvas.git 2>/dev/null || (cd claude-canvas && git pull)`

2. Install dependencies:
!`cd ~/tools/claude-canvas && bun install && cd canvas && bun install`

3. Verify installation:
!`cd ~/tools/claude-canvas && bun run canvas/src/cli.ts env`

Setup complete! You can now use /canvas:weather, /canvas:calendar, etc.
