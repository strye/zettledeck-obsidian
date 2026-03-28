# Obsidian — Metadata and Tags

## `properties` — Read YAML Frontmatter

```bash
# Read all properties from a note
obsidian properties file="Note Name"

# Read vault-wide property list with counts
obsidian properties counts sort=count

# Read a specific property value
obsidian property:read name="status" file="Note Name"
```

**When to use**: Inspecting YAML frontmatter, auditing which properties are in use across the vault.

---

## `property:set` / `property:remove` — Modify YAML Properties

```bash
# Set a property (name= and value= are required)
obsidian property:set name="status" value="active" file="Note Name"

# Set with explicit type
obsidian property:set name="priority" value="high" type=text file="Note Name"
# type options: text | list | number | checkbox | date | datetime

# Remove a property
obsidian property:remove name="draft" file="Note Name"
```

**When to use**: Updating YAML frontmatter without touching note body. Preserves all other frontmatter fields.

---

## `tags` — Tag Management

```bash
# List all tags across the vault
obsidian tags

# List tags with counts
obsidian tags counts sort=count

# Get info on a specific tag
obsidian tag name="aws"

# List tags for a specific file
obsidian tags file="Note Name"
```

**When to use**: Vault-wide tag audit, finding which notes use a tag.

**Note**: `tags:rename` does NOT exist in the CLI. To rename tags, use search + edit the files directly.
