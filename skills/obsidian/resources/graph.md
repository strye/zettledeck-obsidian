# Obsidian — Links and Graph

## `links` — Outgoing Links

```bash
# Outgoing links from a note
obsidian links file="Note Name"

# Count outgoing links
obsidian links file="Note Name" total
```

**When to use**: Understanding what a note connects to, navigating outward from a document.

---

## `backlinks` — Incoming Links

```bash
# Incoming backlinks to a note
obsidian backlinks file="Note Name"

# Backlinks with counts
obsidian backlinks file="Note Name" counts
```

**When to use**: Understanding what refers to a note. Important to check before renaming or deleting.

---

## `orphans` — Notes With No Incoming Links

```bash
obsidian orphans
```

**When to use**: Vault hygiene — finding disconnected notes that may need linking or archiving.

---

## `deadends` — Notes With No Outgoing Links

```bash
obsidian deadends
```

**When to use**: Finding stub notes with no connections outward — candidates for development or deletion.

---

## `unresolved` — Broken Wikilinks

```bash
obsidian unresolved
```

**When to use**: Fixing broken links after renames or moves. Run after any bulk reorganization.
