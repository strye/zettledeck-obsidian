# Obsidian-Specific Frontmatter Conventions

These conventions apply when creating or updating notes in Obsidian. They are in addition to the universal ZettleDeck frontmatter spec defined in `zettledeck/resources/vault-steering.md`.

---

## cssClasses

Obsidian uses the `cssClasses` frontmatter property to apply CSS classes to the note view. ZettleDeck uses this to enable the **dashboard** layout for container-type documents.

### Rule

Add `cssClasses: ["dashboard"]` to any document that acts as a container or hub — one that you navigate *from* rather than read linearly.

### Which document types use it

| docType | Use cssClasses? | Reason |
|---------|----------------|--------|
| `scope` | **Yes** | Domain anchor — hub for all related documents |
| `focus` | **Yes** | Thematic hub linking projects and objectives |
| `project` | **Yes** | Project hub linking deliverables and meetings |
| `objective` | No | Leaf-level document, read linearly |
| `content` | No | Produced artifact, read linearly |
| `meeting` | No | Notes document, read linearly |
| `note` | No | Attached notes, read linearly |
| `ideation` | No | Brainstorm capture, read linearly |
| `research` | No | Research notes, read linearly |

### Frontmatter example

```yaml
---
aliases:
  - Career Development
creationDate: Saturday 1st March 2026
timestamp: 20260301120000
root: "1001"
zettldex: "1001.S"
docType: scope
subType: career
tags:
  - "1001.S"
  - "1001"
  - scope
  - career
scope: "1001"
scopeFile: S1001_CareerDevelopment
status: steady
cssClasses:
  - dashboard
---
```

### When to omit

If the user has disabled dashboard views or is using a custom theme that doesn't support the dashboard class, omit `cssClasses` entirely — it has no effect without the corresponding CSS.
