# zettledeck-obsidian

Obsidian CLI integration module for ZettleDeck. Provides vault interaction skills — search, read, create, move, manage tags, links, tasks, and metadata — via the Obsidian command line interface.

## What This Is

`zettledeck-obsidian` is an add-on module for [zettledeck-core](https://github.com/strye/zettledeck-core). It bridges ZettleDeck's methodology with Obsidian's native CLI, letting your AI tool operate directly on the vault (search, create notes, toggle tasks, inspect the graph) while respecting all ZettleDeck conventions.

This module is intentionally separate from core so that users running a different tool (or no tool) are not required to install Obsidian tooling.

## Requirements

- [zettledeck-core](https://github.com/strye/zettledeck-core) installed and initialized
- Obsidian 1.12.4 or later
- Obsidian running in the background during vault operations
- CLI registered: Obsidian → Settings → General → Command line interface → Register CLI

## Installation

Add to `.zettledeck/zettledeck.yml` in your vault project:

```yaml
modules:
  - name: zettledeck-obsidian
    repo: github.com/strye/zettledeck-obsidian
    ref: main
```

Then install:

```bash
.zettledeck/scripts/zd install
```

Then run the obsidian init step to confirm CLI registration:

```
/zettledeck.init obsidian
```

## Configuration

`.zettledeck/zettledeck-obsidian/config.json` (created by `/zettledeck.init obsidian`):

```json
{
  "cliRegistered": true
}
```

Vault name and path are read from `.zettledeck/core/config.json` — no duplication needed.

## Skills

### obsidian

Interact with the Obsidian vault via the `obsidian` CLI. Loaded automatically when the user requests vault operations, or invoked directly:

```
/obsidian [mode] [args]
```

Resources are loaded on demand — the skill routes to the relevant file rather than loading everything at once.

| Resource | Operations |
|----------|-----------|
| `find.md` | `search`, `read`, `outline`, `files`, `recents`, `folders` |
| `write.md` | `create`, `append`, `prepend` |
| `organize.md` | `move`, `rename`, `delete`, `open` |
| `metadata.md` | `properties`, `property:read`, `property:set`, `property:remove`, `tags` |
| `graph.md` | `links`, `backlinks`, `orphans`, `deadends`, `unresolved` |
| `tasks.md` | `tasks`, `task` |
| `vault.md` | `vault`, `eval` |
| `workflows.md` | Search→Read→Act, Vault Hygiene, Task Audit |
| `obsidian-conventions.md` | Obsidian-specific frontmatter (`cssClasses`) |

### CLI Syntax

- Flags are bare keywords, not `--` prefixed (e.g. `overwrite` not `--overwrite`)
- Quote values with spaces: `name="My Note"`
- `file=` resolves by name (like wikilinks); `path=` is exact (`folder/note.md`)

## Tool Compatibility

Follows the same tool wiring as zettledeck-core. `zd install` copies skills into `.shared/skills/obsidian/` and auto-wires any agent assets.

- **Claude Code** — skill available via `.claude/skills/obsidian`
- **Kiro** — skill available via `.kiro/skills/obsidian`

## License

MIT
