---
name: finalize
description: Generate the final documentation files (features.md, CLAUDE.md, progress.md)
argument-hint: ""
allowed-tools: ["Read", "Write", "Bash", "Glob", "Grep", "TodoWrite"]
---

# Finalize: Generate Documentation

Create the final output files that will guide development.

## Prerequisites

This step requires a completed `/app-creator:review` session where the user confirmed the feature list is complete.

If no confirmed feature list exists, inform the user to complete the earlier steps first.

## Load Templates

Read the file templates:
- `app-creator/skills/app-discovery/references/templates.md` - Doc file templates
- `app-creator/skills/app-discovery/references/package-templates.md` - Package config templates
- `app-creator/skills/app-discovery/references/progress-template.md` - Progress structure

Use these templates as the basis for the output files.

## Create Output Directory

Check if `docs/` directory exists:

```bash
ls docs/ 2>/dev/null || mkdir -p docs
```

Create the directory if it doesn't exist.

## Generate Files

### 1. docs/features.md

Create the complete feature list file:

1. Use the template from `references/templates.md`
2. Include all features from the review
3. Set all statuses to 🔴 Not Started
4. Include the feature count in header
5. Set "Last Updated" to current date
6. Preserve the "How to Use This File" section
7. Include the template comment at the end

### 2. CLAUDE.md

Create the project context file:

1. Use the template from `references/templates.md`
2. Fill in project name and overview
3. Document the tech stack decisions
4. Leave "Project Structure" to be filled after scaffolding
5. Include the workflow instructions
6. Add any architecture decisions discussed
7. Note any conventions mentioned

### 3. docs/progress.md

Create the progress log:

1. Use the template from `references/templates.md` and `references/progress-template.md`
2. Document the discovery session
3. Include key decisions made
4. Summarize the app overview
5. List feature count (total, core, nice-to-have)
6. Document tech stack decisions
7. Add next steps checklist

### 4. package.json or pyproject.toml

Generate the package configuration based on tech stack:

1. Read `references/package-templates.md` for templates
2. Determine if Node/Python from CLAUDE.md tech stack
3. Start with base template for that stack
4. Add dependencies identified during discovery (from features, analyze, breakdown)
5. Include testing libraries (vitest for Node, pytest for Python)
6. Keep minimal — only what's needed for v1

**For Node projects:** Create `package.json` at project root
**For Python projects:** Create `pyproject.toml` at project root

Do NOT run install commands — that's dev-protocol:init's job.

## File Locations

Write files to:
- `./CLAUDE.md` (project root)
- `./docs/features.md`
- `./docs/progress.md`
- `./package.json` or `./pyproject.toml` (based on tech stack)

## Output Summary

After creating files, display:
- Confirmation of files created
- Feature count
- Suggested next steps

## Next Steps Guidance

Inform the user:

1. **Review the files** - Make sure everything looks right
2. **Commit to git** - `git add . && git commit -m "Initial discovery documentation"`
3. **Run `/dev-protocol:init`** - Installs dependencies and sets up sprint infrastructure
4. **Run `/dev-protocol:sprint`** - Begin building Feature 1
5. **Use `/app-creator:revise`** - When features need updating during development

## Completion Message

```
Discovery complete! Created:
- CLAUDE.md (project context)
- docs/features.md (N features with tests)
- docs/progress.md (session summary)
- package.json (or pyproject.toml) with dependencies

Next: Run `/dev-protocol:init` to scaffold the project and install dependencies.

During development, use `/app-creator:revise` to update features based on what you learn.
```

## Error Handling

If file already exists:
- Warn the user before overwriting
- Offer to create backup (e.g., `features.md.backup`)
- Only proceed with explicit confirmation
