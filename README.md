# Refresh

A [Claude Code](https://claude.ai/claude-code) skill that refreshes marketplaces, updates installed plugins, and reloads the session in one shot.

## Installation

### Via Marketplace

```bash
claude plugin marketplace add HurleySk/claude-plugins-marketplace
claude plugin install refresh
```

### Direct

```bash
claude plugin add HurleySk/claude-refresh-skill
```

## Commands

| Command | Description |
|---------|-------------|
| `/refresh` or `/refresh all` | Refresh marketplaces + update all plugins + remind to reload |
| `/refresh marketplace` | Refresh marketplace registries only |
| `/refresh plugins` | Update installed plugins only |
| `/refresh status` | Show current marketplace and plugin state |
| `/refresh help` | Show available commands |

## License

MIT
