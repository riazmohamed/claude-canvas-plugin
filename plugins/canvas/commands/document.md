---
allowed-tools: Bash(bun:*), Bash(cd:*)
description: Spawn a markdown document canvas with optional content
argument-hint: Optional markdown content to display
---
Spawn a document canvas with optional content:
!`cd ~/tools/claude-canvas && bun run canvas/src/cli.ts spawn document --config '{"content":"$ARGUMENTS"}'`
