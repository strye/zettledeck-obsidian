# Obsidian — Task Operations

## `tasks` — List Tasks Across the Vault

```bash
# All tasks (open and closed)
obsidian tasks

# Completed tasks only
obsidian tasks done

# Incomplete tasks only
obsidian tasks todo

# Tasks in a specific file
obsidian tasks file="Note Name"

# JSON output for structured processing
obsidian tasks format=json

# Grouped by file with line numbers
obsidian tasks verbose
```

**When to use**: Getting a cross-vault task view. Use `verbose` to get line numbers for follow-up `task` operations.

---

## `task` — Single Task Operations

```bash
# Toggle task status
obsidian task path="path/to/note.md" line=42 toggle

# Mark done
obsidian task path="path/to/note.md" line=42 done

# Mark incomplete
obsidian task path="path/to/note.md" line=42 todo

# Set a custom status character
obsidian task path="file.md" line=42 status="/"
```

**Note**: `task:create` does NOT exist — create tasks by appending markdown to a note with `obsidian append`.

**Task format**: Always use the Obsidian Tasks emoji signifier format when creating tasks via `append`. See `markdown/task-format.md` for the full format specification.
