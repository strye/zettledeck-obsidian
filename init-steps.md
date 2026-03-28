---
module: obsidian
order: 15
description: Verify Obsidian CLI registration and confirm vault name and path
---

## Configuration Convention

Obsidian-specific configuration is stored in `.zettledeck/zettledeck-obsidian/config.json`. This is where vault identity lives — the vault name and path that the CLI uses to locate and open the correct vault.

### Config file format

**File:** `.zettledeck/zettledeck-obsidian/config.json`

```json
{
  "vaultName": "Reliquary",
  "vaultPath": "Reliquary",
  "cliRegistered": true
}
```

- **`vaultName`** — The display name of the vault as it appears in Obsidian
- **`vaultPath`** — Path to the vault root folder, relative to the project root (default: `Reliquary`)
- **`cliRegistered`** — Set to `true` once the CLI registration is confirmed

---

## Step 1 — Vault Identity

**What:** Establish the vault name and path so the obsidian CLI can locate the correct vault.

**Config keys:** `vaultName`, `vaultPath`

### Questions to ask the user

1. "What is the name of your Obsidian vault?"
   - Default: the project directory name

2. "Where is the vault root — is it a subfolder of the project, or is it the project root itself?"
   - Default: `Reliquary` (standard ZettleDeck layout)
   - If different: ask for the relative path

### How to apply

Write `vaultName` and `vaultPath` to `.zettledeck/zettledeck-obsidian/config.json`.

---

## Step 2 — CLI Registration Check

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

## Step 3 — Vault Path Confirmation

**What:** Confirm the vault Obsidian should open matches what is configured.

### Questions to ask the user

1. "Your vault path is set to `{vaultPath}`. Is this the vault currently open in Obsidian?"
   - Yes: no action needed
   - No: remind user to switch vaults in Obsidian, or update `vaultPath` in `.zettledeck/zettledeck-obsidian/config.json`
