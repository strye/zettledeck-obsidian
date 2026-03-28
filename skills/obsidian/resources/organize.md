# Obsidian — Organizing Notes

## `move` — Move a Note to a Different Folder

```bash
# Move to a different folder
obsidian move file="Draft Note" to="Archive/2025/"

# Move using exact path
obsidian move path="path/to/old.md" to="Archive/2025/old.md"
```

**When to use**: Reorganizing vault structure. Preserves wikilinks automatically.

**Always confirm** with user before moving files. For renaming (same folder, new name), use `rename` instead.

---

## `rename` — Rename a Note

```bash
obsidian rename file="Old Name" name="New Name"
obsidian rename path="path/to/old.md" name="New Name"
```

**When to use**: Renaming a note in place (same folder). Preserves wikilinks automatically. Use `move` when changing folders.

**Always confirm** before renaming — it affects all backlinks. Warn the user if the note is linked from many other notes.

---

## `delete` — Delete a Note

```bash
# Move to Obsidian trash (default, recoverable)
obsidian delete file="Old Note"

# Permanent delete (irreversible)
obsidian delete file="Old Note" permanent
```

**NEVER use `permanent`** without explicit user instruction. Default trash behavior is always preferred.

**Always confirm** before deleting.

---

## `open` — Open a File in Obsidian

```bash
obsidian open file="Note Name"
obsidian open file="Note Name" newtab
```

**When to use**: User wants to navigate to a note in the Obsidian UI without reading its content via CLI.
