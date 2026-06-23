---
name: vault-organization
description: Organize an Obsidian vault by normalizing YAML frontmatter headers and relocating misplaced files to their correct directories.
---

This skill provides a systematic workflow to audit and organize an Obsidian vault. Use it when the vault has inconsistent or missing YAML frontmatter, or when files are scattered outside their logical directory structure.

The user provides the vault root path. The skill produces a consistently organized vault where every markdown file has proper headers and a correct directory placement.

## Workflow

### 1 — Analyze vault structure
- List all `.md` files across the vault using `find`
- Identify the Obsidian YAML frontmatter pattern: `---` delimiters with `tags` and `created` fields
- Map out directory categories

### 2 — Find files missing headers
- Use `grep -q "^---$"` on every file to detect YAML frontmatter
- Compile list of files without headers

### 3 — Add headers to missing files
- Pattern match the header format used elsewhere in the vault
- Add `tags` (topic-specific) and `created` date (taken from file system modification timestamps)

### 4 — Find files outside their logical folders
- Analyze file content for wiki-link relationships to determine correct folder
- Identify files at the top level or in mismatched directories

### 5 — Re-scan after moves
- Re-run header detection scan to catch any files previously missed or newly displaced
- Ensure no regressions

### 6 — Propose plan to user
- Present file moves and header additions as a clear proposal
- Include rationale for each move based on content and cross-references

### 7 — Execute remaining changes
- Move files to correct directories
- Add headers to any remaining files
- Verify all files have headers and are in correct locations
