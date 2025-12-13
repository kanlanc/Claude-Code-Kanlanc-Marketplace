# Kanlanc Claude Code Plugin Marketplace

A collection of Claude Code plugins for enhanced development workflows.

## Available Plugins

| Plugin | Description |
|--------|-------------|
| [codex-consulting](./codex-consulting/) | Consult OpenAI Codex (gpt-5.2) for second opinions, code analysis, and expert insights |

## Installation

Install any plugin from this marketplace:

```bash
claude plugins add kanlanc/Claude-Code-Kanlanc-Marketplace/<plugin-name>
```

For example:
```bash
claude plugins add kanlanc/Claude-Code-Kanlanc-Marketplace/codex-consulting
```

## Plugins vs MCP

| Aspect | Plugins | MCP |
|--------|---------|-----|
| **Format** | Markdown files | Python/TypeScript server |
| **Invocation** | `/command` | `mcp__server__tool` |
| **Best for** | CLI wrappers, workflows | External APIs, stateful services |
| **Complexity** | Simple | More involved |
| **State** | Use native CLI features | Custom state management |

**When to use Plugins**: CLI tool wrappers, simple command extensions, workflows that leverage native CLI session management.

**When to use MCP**: Complex integrations, real-time data sources, external APIs, custom server logic.

## Contributing

Add your own plugins by creating a new directory with the standard plugin structure:

```
your-plugin/
├── .claude-plugin/
│   └── plugin.json
├── README.md
├── commands/
├── skills/
└── agents/
```

## License

MIT
