# Obsidian — Finding Content

## `search` — Full-Text and Structured Search

```bash
# Full-text search
obsidian search query="customer discovery"

# Tag search
obsidian search query="[tag:customer]"

# Property/frontmatter search
obsidian search query="[status:active]"

# Combined
obsidian search query="migration [tag:aws]"

# Limit results
obsidian search query="topic" limit=10

# JSON output (for parsing)
obsidian search query="topic" format=json

# Case sensitive
obsidian search query="AWS" case

# Search with surrounding line context
obsidian search:context query="customer discovery"
obsidian search:context query="topic" format=json
```

**When to use**: Finding notes by content, tag, or metadata. Use `search:context` when you need to see matching lines in context. If the exact name is unknown, use `search` first, then `read`.

---

## `read` — Read Note Content

```bash
obsidian read file="Note Name"
obsidian read path="path/to/note.md"
```

**When to use**: User wants to see the content of a specific note. Use exact note name (no `.md` extension needed with `file=`).

---

## `outline` — Show Note Headings

```bash
# Show headings as a tree
obsidian outline file="Note Name"

# Markdown format
obsidian outline file="Note Name" format=md

# JSON format
obsidian outline file="Note Name" format=json

# Count headings
obsidian outline file="Note Name" total
```

**When to use**: Navigating a long note, getting a structural overview before reading or editing.

---

## `files` — List and Count Notes

```bash
# List all notes
obsidian files

# List notes in a specific folder
obsidian files folder="path/to/folder"

# Filter by extension
obsidian files ext=md

# Count total notes
obsidian files total
```

**When to use**: Vault exploration, finding notes in a folder, getting counts.

---

## `recents` — Recently Opened Files

```bash
obsidian recents
obsidian recents total
```

**When to use**: Finding recently worked-on files without a specific search query.

---

## `folders` — Folder Operations

```bash
# Show folder info
obsidian folder path="path/to/folder"

# List subfolders
obsidian folders folder="path/to/parent"

# Count folders
obsidian folders total
```

**When to use**: Navigating vault folder structure, counting notes in a section.
