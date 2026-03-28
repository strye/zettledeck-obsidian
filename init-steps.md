---
module: obsidian
order: 15
description: Verify Obsidian CLI registration and confirm vault path
---

## Configuration Convention

Obsidian-specific configuration is stored in `.zettledeck/zettledeck-obsidian/config.json`. Vault path and name are read from `.zettledeck/core/config.json` — no duplication needed.

### Config file format

**File:** `.zettledeck/zettledeck-obsidian/config.json`

```json
{
  "cliRegistered": true
}
```

---

## CLI Registration Check

**What:** Verify the Obsidian CLI is registered and reachable so vault skills work correctly.

**Config key:** `cliRegistered`

### Questions to ask the user

1. "Let's confirm the Obsidian CLI is set up. Run this in your terminal and tell me what you see:"
   ```bash
   obsidian help
   ```
   - If it returns help text: CLI is registered — proceed
   - If `command not found`: walk through registration steps below

### Registration steps (if needed)

1. Open Obsidian
2. Go to Settings → General → Command line interface
3. Click **Register CLI**
4. Restart your terminal or run `source ~/.zshrc` (or your shell profile)
5. Re-run `obsidian help` to confirm

### How to apply

Write `cliRegistered: true` to `.zettledeck/zettledeck-obsidian/config.json` once confirmed.

---

## Vault Path Confirmation

**What:** Confirm the vault Obsidian should open. Uses `vaultPath` from `.zettledeck/core/config.json`.

### Questions to ask the user

1. "Your vault path is set to `{vaultPath}` (from core config). Is this the vault currently open in Obsidian?"
   - Yes: no action needed
   - No: remind user to switch vaults in Obsidian, or update `vaultPath` in `.zettledeck/core/config.json`
