---
name: obsidian
description: Interact with the Obsidian vault using the obsidian CLI — read, search, create, move, manage tags/links/tasks, and inspect metadata. Works across all modes- notes, search, tasks, properties, and links.
---

# Obsidian — CLI Vault Operations

Interact with the Obsidian vault directly via the `obsidian` CLI. Load the relevant resource file for the operation you need — don't load all resources at once.

## Invocation

Call this skill when the user requests vault operations:

- "Search my vault for [topic]" → load `resources/find.md`
- "Read the note [Note Name]" → load `resources/find.md`
- "Create a note called [Name]" → load `resources/write.md`
- "Append [content] to [note]" → load `resources/write.md`
- "Move / rename / delete [note]" → load `resources/organize.md`
- "Set the [property] on [note]" → load `resources/metadata.md`
- "Show backlinks / orphans / graph" → load `resources/graph.md`
- "List / toggle tasks" → load `resources/tasks.md`
- "Vault info / stats" → load `resources/vault.md`
- "Show me how to [workflow]" → load `resources/workflows.md`
- `/obsidian [mode] [args]`

## Resource Files

| Resource | Modes covered |
|----------|--------------|
| `resources/find.md` | `search`, `read`, `outline`, `files`, `recents`, `folders` |
| `resources/write.md` | `create`, `append`, `prepend` |
| `resources/organize.md` | `move`, `rename`, `delete`, `open` |
| `resources/metadata.md` | `properties`, `property:read`, `property:set`, `property:remove`, `tags` |
| `resources/graph.md` | `links`, `backlinks`, `orphans`, `deadends`, `unresolved` |
| `resources/tasks.md` | `tasks`, `task` |
| `resources/vault.md` | `vault`, `eval` |
| `resources/workflows.md` | Search→Read→Act, Vault Hygiene, Task Audit |
| `resources/obsidian-conventions.md` | cssClasses, Obsidian-specific frontmatter |

---

## Requirements

- Obsidian 1.12.4 or later (installer updates at obsidian.md/download)
- Obsidian must be **running in the background**
- CLI registered: Obsidian → Settings → General → Command line interface → Register CLI
- Vault path configured in `.zettledeck/zettledeck-obsidian/config.json` (`vaultPath`)

**Tools needed**: Bash, Read, Write, Glob

## Setup Check

Before any CLI command, verify the CLI is available:

```bash
obsidian help 2>&1
```

If `command not found`:
1. Open Obsidian → Settings → General → Command line interface → Register CLI
2. Restart terminal / source shell profile
3. Retry

If Obsidian is not running, ask the user to open it before proceeding.

---

## CLI Syntax Notes

- Flags are bare keywords, NOT prefixed with `--` (e.g. `overwrite` not `--overwrite`)
- Quote values with spaces: `name="My Note"`
- Use `\n` for newline, `\t` for tab in content values
- `file=` resolves by name (like wikilinks); `path=` is exact (e.g. `folder/note.md`)
- Most commands default to the active file when `file`/`path` is omitted

---

## Output Formats

| Format | Use |
|--------|-----|
| `format=json` | Machine-readable, for parsing in workflows |
| `format=csv` | Spreadsheet export |
| `format=tsv` | Tab-separated (default for many list commands) |
| `format=md` | Markdown-formatted output |
| `format=yaml` | YAML structure (default for `properties`) |
| `format=tree` | Folder tree view (e.g. `outline`) |

---

## Error Handling

| Error | Action |
|-------|--------|
| `command not found: obsidian` | Guide user through CLI registration (see Setup Check) |
| `Note not found` | Try `obsidian search` to find the correct note name |
| `Obsidian is not running` | Ask user to open Obsidian and retry |
| `Permission denied` | Check CLI registration in Obsidian settings |
| File not found via CLI but exists on disk | CLI only sees indexed notes — open Obsidian to trigger indexing |
| search/version commands return no output | Installer version mismatch — download latest from obsidian.md/download, reinstall and restart |
| `vault=<name>` returns nothing | `vault=` only works for non-app-context commands. Switch to the vault in Obsidian first, then run without `vault=` |

---

## Boundaries

**Always:**
- Follow recommend-first principle — propose actions before executing
- Preserve frontmatter on all note operations
- Use `append` over `create overwrite` when adding to existing notes
- Follow vault structure from `.zettledeck/core/config.json` and rules from `zettledeck/resources/vault-steering.md`
- Use bare flags (no `--` prefix)
- Apply `cssClasses` per `resources/obsidian-conventions.md` when creating container-type documents

**Ask First:**
- Before creating, moving, renaming, or deleting any note
- Before appending significant content to planning files

**Never:**
- Use `permanent` delete without explicit user instruction
- Overwrite notes with `overwrite` without confirmation
- Run `obsidian eval` with destructive JavaScript
- Rename or move heavily-linked notes without warning the user about link impact
- Use `tags:rename` (it doesn't exist) — edit files directly instead
