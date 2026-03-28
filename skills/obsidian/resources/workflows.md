# Obsidian — Common Workflows

## Search → Read → Act

The standard pattern for any vault operation:

1. **Search** to find relevant notes
2. **Read** to inspect content
3. **Propose** the action (recommend-first)
4. **Execute**

```bash
# Step 1: Find candidate notes
obsidian search query="customer migration"

# Step 2: Read the top result
obsidian read file="Migration Plan"

# Step 3: Propose action to user
# "Found the migration plan. I can append these action items. Shall I?"

# Step 4: Execute
obsidian append file="Migration Plan" content="..."
```

---

## Vault Hygiene

Periodic health check to find disconnected and broken notes:

```bash
# 1. Find orphan notes (no incoming links)
obsidian orphans

# 2. Find dead-end notes (no outgoing links)
obsidian deadends

# 3. Find broken wikilinks
obsidian unresolved

# 4. Audit tags
obsidian tags counts sort=count

# 5. Count notes by folder
obsidian files folder="path/to/folder" total
```

Present findings and propose cleanup actions. Never delete or rename without approval.

---

## Task Audit

Get a cross-vault view of open tasks:

```bash
# All incomplete tasks
obsidian tasks todo

# Grouped by file with line numbers (useful for follow-up)
obsidian tasks todo verbose

# JSON for structured processing
obsidian tasks todo format=json
```

Present a summarized list, grouped by priority or date. Propose next actions.
