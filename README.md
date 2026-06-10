# claude-code — CodeCrafters Automation

Everything CodeCrafters Automation OU builds for [Claude Code](https://code.claude.com/docs/) in one place: plugins, MCP servers, and standalone skills.

```
.
├── .claude-plugin/
│   └── marketplace.json     # plugin marketplace catalog (lives at repo root)
├── plugins/                 # Claude Code plugins (the marketplace)
│   └── ccp/                 #   → Change Claude Profile
├── mcp/                     # MCP servers
├── skills/                  # standalone Agent Skills
├── .gitignore
└── README.md
```

> **Why the catalog is at the root:** a Claude Code marketplace is identified by `.claude-plugin/marketplace.json` at the repo root, and plugin `source` paths resolve relative to it (each entry points to `./plugins/<name>`). It only ever references `plugins/` — the `mcp/` and `skills/` directories sit alongside it untouched, free for you to grow.

## Plugins (the marketplace)

Add the marketplace once, then install any plugin from it:

```
/plugin marketplace add codecraftersautomation/claude-code
/plugin install <plugin-name>@codecraftersautomation
/reload-plugins
```

This registers a marketplace named `codecraftersautomation`.

### Available plugins

| Plugin | Install | What it does |
|--------|---------|--------------|
| **Change Claude Profile** (`ccp`) | `/plugin install ccp@codecraftersautomation` | Hand off and take over work between two Claude Code profiles (`claude-team` ⇄ `claude-max`) from the same repo, and keep their plugins aligned — without ever copying credentials, OAuth tokens, or plugin cache. |

Full purpose and how-to-use for each plugin lives in that plugin's own README — see [`plugins/ccp/README.md`](plugins/ccp/README.md). (Per-plugin docs ship and version with the plugin; this root README is just the index.)

## MCP servers

Standalone or plugin-bundled MCP servers live under [`mcp/`](mcp/). _None yet._

## Skills

Standalone Agent Skills (not tied to a plugin) live under [`skills/`](skills/). _None yet._

## Local development

From a clone, add the marketplace by path instead of by `owner/repo`:

```
/plugin marketplace add /path/to/claude-code
/plugin install <plugin-name>@codecraftersautomation
/reload-plugins
```

Validate before publishing:

```
claude plugin validate ./plugins/<name> --strict   # a plugin
claude plugin validate .                            # the marketplace catalog
```

## Maintainers

- Owner: **CodeCrafters Automation OU**
- Author: **Jairo Escobar**
- Contact: open an issue on this repository.

## License

MIT.
