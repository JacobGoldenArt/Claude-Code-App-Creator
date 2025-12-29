# App Creator Plugin

A Claude Code plugin for clarifying app ideas and breaking them into atomic, testable features before writing any code.

## Overview

App Creator guides you through a structured discovery process:

1. **Start** - Brainstorming interview to capture your app vision
2. **Analyze** - Solidify the concept and identify potential issues
3. **Breakdown** - Decompose features into binary testable items
4. **Review** - Refine until "yes, that's my app"
5. **Finalize** - Generate structured documentation

## Commands

| Command | Description |
|---------|-------------|
| `/app-creator:start` | Begin the discovery interview |
| `/app-creator:analyze` | Solidify app concept and find logic holes |
| `/app-creator:breakdown` | Break features into detailed tests |
| `/app-creator:review` | Review and refine the feature list |
| `/app-creator:finalize` | Generate output files |
| `/app-creator:revise` | Update features based on development learnings |

## Workflow

Run commands sequentially: `start` → `analyze` → `breakdown` → `review` → `finalize`

The `/revise` command can be run anytime after the initial flow to update features based on what you learn during development.

## Output

Creates the following files in `docs/`:

- `features.md` - Complete feature list with binary tests
- `CLAUDE.md` - Project overview and tech stack
- `progress.md` - Session summary

## Installation

```bash
claude --plugin-dir /path/to/app-creator
```

Or copy to your project's `.claude-plugin/` directory.
