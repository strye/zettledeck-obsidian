# Obsidian — Vault-Level Commands

## `vault` — Vault Info

```bash
# Full vault summary
obsidian vault

# Specific info fields
obsidian vault info=name
obsidian vault info=path
obsidian vault info=files
obsidian vault info=size
```

**When to use**: Quick vault stats, confirming which vault is active, verifying the vault path matches `.zettledeck/core/config.json`.

---

## `eval` — Execute JavaScript in Obsidian

```bash
obsidian eval code="app.vault.getFiles().length"
```

**When to use**: Advanced debugging, plugin development, or operations not covered by standard commands.

**Use sparingly** — prefer specific commands. Never run `eval` with destructive JavaScript without explicit user confirmation.
