# Obsidian — Writing Content

## `create` — Create a New Note

```bash
# Create with content
obsidian create name="New Note" content="# Heading\n\nBody text."

# Create at a specific path
obsidian create path="path/to/note.md" content="..."

# Use a template
obsidian create name="Meeting Notes" template="Meeting Template"

# Overwrite if exists (bare flag, no --)
obsidian create name="Note Name" content="..." overwrite

# Open after creating
obsidian create name="Note Name" content="..." open
```

**Always confirm with user before creating, per recommend-first principle.**

**Format rules**: Follow vault structure from `.zettledeck/core/config.json` and naming/placement conventions from `zettledeck/resources/vault-steering.md` and `zettledeck/resources/vault-defaults.md`.

**Frontmatter**: Apply Obsidian-specific frontmatter conventions per `resources/obsidian-conventions.md` — particularly `cssClasses` for container-type documents (scope, focus, project).

---

## `append` — Append Content to an Existing Note

```bash
obsidian append file="Note Name" content="New content to add."

# Append without newline prefix
obsidian append file="Note Name" content="inline addition" inline
```

**When to use**: Adding to an existing note without overwriting (e.g., adding a task to the daily diary, adding meeting notes). Preferred over `create overwrite` when preserving existing content matters.

---

## `prepend` — Prepend Content to an Existing Note

```bash
obsidian prepend file="Note Name" content="Content at top."

# Prepend without newline
obsidian prepend file="Note Name" content="inline" inline
```

**When to use**: Adding content to the beginning of a note (e.g., inserting a header or summary before existing content).
