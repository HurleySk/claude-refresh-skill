---
name: refresh
description: Refresh marketplaces, update installed plugins, and reload in one shot. Use when the user says "refresh plugins", "update plugins", "sync marketplace", or after pushing changes to a plugin repo.
argument-hint: "[all|marketplace|plugins|status|help]"
---

# Refresh

You refresh Claude Code marketplaces, update installed plugins, and reload the session. Follow the steps below exactly.

## Commands

### `all` (default — used when no argument given)

Run all three phases in order: marketplace → plugins → reload.

#### Phase 1: Refresh Marketplaces

```bash
claude plugin marketplace update 2>&1
```

This pulls the latest `marketplace.json` from every configured marketplace source. Report which marketplaces were updated.

#### Phase 2: Update Installed Plugins

First, list installed plugins and capture which marketplace each came from:

```bash
claude plugin list 2>&1
```

Then update each enabled plugin individually. `claude plugin update` requires a specific plugin name — there is no `--all` flag. Update them one at a time:

```bash
claude plugin update <plugin-name> 2>&1
```

Do this for every enabled plugin from the list. Skip disabled plugins. Report the result of each update (version change, already up-to-date, or error).

#### Phase 3: Reload Plugins

Tell the user:

> Marketplaces refreshed and plugins updated. To reload plugins in this session, run `/reload-plugins` in the prompt. (This is a built-in Claude Code command that can't be invoked programmatically.)

### `marketplace`

Run Phase 1 only — refresh marketplace registries without updating plugins.

### `plugins`

Run Phase 2 only — update installed plugins without refreshing marketplaces first.

### `status`

Show current state without changing anything:

```bash
claude plugin marketplace list 2>&1
```

```bash
claude plugin list 2>&1
```

Present the output in a clean summary: marketplace sources with their types, installed plugins with versions and enabled/disabled status.

### `help`

Show available commands:

| Command | Description |
|---------|-------------|
| `/refresh` or `/refresh all` | Refresh marketplaces + update all plugins + remind to reload |
| `/refresh marketplace` | Refresh marketplace registries only |
| `/refresh plugins` | Update installed plugins only |
| `/refresh status` | Show current marketplace and plugin state |
| `/refresh help` | Show this help |
