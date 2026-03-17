---
description: Strip robot language from user-facing content - fix terminology, tone, and phrasing
---

# Humanize

Scan and fix machine-generated writing patterns in user-facing content.

## Execute

Scan the target files for machine-generated writing indicators and fix them.

### Target

If `$ARGUMENTS` specifies a file or directory, use that. Otherwise, scan the current working directory for:
- README.md
- CHANGELOG.md
- Any `.md` files in `docs/`
- Package descriptions in `package.json`, `pyproject.toml`

Skip: CLAUDE.md files, code files, generated files, license files.

### Process

1. **Checkpoint** — `git add -A && git commit -m "checkpoint before humanization"` (if there are uncommitted changes)
2. **Scan** — Apply the 15 detection patterns from the humanize skill
3. **Fix** — Auto-fix high-confidence patterns (>0.9), suggest medium-confidence (0.7-0.9), flag low-confidence (<0.7)
4. **Report** — Show a summary of changes made and suggestions

### What to Look For

- "AI-powered", "AI-enhanced", "AI-driven" or "AI" as a noun
- "leverages", "utilizes", "facilitates" (use "uses", "helps", "runs")
- "seamless", "robust", "cutting-edge" (describe what it does instead)
- "we" in solo developer contexts (use "I")
- Em-dashes used for dramatic pauses
- Passive voice where active is clearer
- Corporate jargon and buzzword clusters
- Stiff constructions ("It is important to note that...")
- Hedge phrases ("might potentially", "could perhaps")

### Output

Show a summary:
```
Humanize: {file}
- {count} patterns auto-fixed
- {count} suggestions for review
- {count} items flagged
```

For each change, show before/after.

## Arguments

- File path or directory (optional, defaults to cwd)
- `--dry-run` — scan and report without making changes
- `--strict` — also fix medium-confidence patterns automatically
