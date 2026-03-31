# Claude Code v2.1.88 Source Code

From npm package `@anthropic-ai/claude-code` version **2.1.88**.

The published package ships a single bundled `cli.js` (~12MB). The `src/` directory in this repo contains the **decompiled/unbundled TypeScript source** extracted from the npm tarball.

## Stats

| Item | Count |
|------|-------|
| Source files (.ts/.tsx) | ~1,884 |
| Lines of code | ~512,664 |
| Dependencies (node_modules) | ~192 packages |

## Directory Structure

```
src/
├── main.tsx                 # Main entry (~4,683 lines)
├── QueryEngine.ts           # Core query lifecycle engine
├── query.ts                 # Query main loop (~785KB, largest file)
├── Tool.ts                  # Tool interface + buildTool factory
├── Task.ts                  # Task types and lifecycle
├── tools.ts                 # Tool registry and presets
├── bridge/                  # Bridge to Claude Desktop / remote
├── cli/                     # CLI handlers and transports
├── commands/                # Slash commands (~80+)
├── components/              # React/Ink terminal UI
├── entrypoints/             # CLI, SDK, MCP entry points
├── hooks/                   # React hooks
├── screens/                 # REPL and other screens
├── services/                # API, analytics, MCP, compact, plugins
├── state/                   # AppState management
├── tasks/                   # Task implementations (bash, agent, remote)
├── tools/                   # Tool implementations (~40+)
│   ├── AgentTool/           # Sub-agent spawning
│   ├── BashTool/            # Shell execution
│   ├── FileEditTool/        # File editing
│   ├── FileReadTool/        # File reading
│   ├── FileWriteTool/       # File writing
│   ├── GlobTool/            # File glob search
│   ├── GrepTool/            # Content grep search
│   ├── MCPTool/             # MCP protocol tools
│   ├── WebFetchTool/        # Web fetching
│   └── ...                  # 30+ more tools
├── types/                   # TypeScript type definitions
├── utils/                   # Utilities
└── vendor/                  # Native module source stubs
```

## Key Architecture

- **Runtime**: Bun (uses `bun:bundle` feature flags, macros)
- **UI**: React + Ink (terminal rendering)
- **API**: Anthropic Claude API with streaming
- **Protocol**: MCP (Model Context Protocol) for tool extensions
- **Build**: Bun bundler produces single `cli.js` with dead code elimination

## Notes

- This source is **not directly compilable** — it lacks `tsconfig.json`, build scripts, and the full Bun build pipeline
- Feature flags (`feature('...')`) are compile-time gated via Bun's dead code elimination
- `process.env.USER_TYPE === 'ant'` sections are Anthropic-internal only
- The compiled `cli.js` is a self-contained bundle requiring only Node.js >= 18

## License

See the original package for license information.
