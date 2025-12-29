---
name: revise
description: Update features and tests based on development learnings
argument-hint: "[what needs to change]"
allowed-tools: ["Read", "Write", "Edit", "Glob", "Grep", "TodoWrite", "AskUserQuestion"]
---

# Revise: Update Features During Development

Update the feature list based on learnings from development. This command can be run anytime after the initial discovery flow is complete.

## Prerequisites

This command requires existing documentation files:
- `docs/features.md`
- `CLAUDE.md`

If these don't exist, inform the user to complete the discovery flow first (`/app-creator:start` through `/app-creator:finalize`).

## When to Use

Use this command when development reveals:
- A feature is too large and needs splitting
- Tests are missing or need updating
- New requirements discovered
- Feature scope needs adjustment
- Dependencies are wrong
- Implementation notes to add

## Revision Process

### 1. Understand the Change

Listen to what the user learned during development:
- What did they discover?
- What needs to change?
- Why is the current spec incorrect?

If the user provided context in the command argument, acknowledge it and ask clarifying questions if needed.

### 2. Read Current State

Read the existing files:
- `docs/features.md` - Current feature definitions
- `docs/progress.md` - Recent development context (optional)

Understand what currently exists before proposing changes.

### 3. Propose Changes

Show the user exactly what will change:

**For feature modifications:**
```
Feature 3: User Authentication

Current:
- [ ] Password must be at least 8 characters

Proposed:
- [ ] Password must be at least 12 characters
- [ ] Password must contain uppercase, lowercase, and number
```

**For new features:**
```
Adding new feature after Feature 5:

### 6. Password Reset

**Status:** 🔴 Not Started

**Description:** Users can reset their password via email link.

**Dependencies:** Feature 3 (User Authentication)

**Tests:**
- [ ] "Forgot password" link visible on login page
- [ ] ...
```

**For feature splits:**
```
Splitting Feature 4 into two features:

### 4. Basic Search
[subset of original tests]

### 5. Advanced Filters (new)
[other subset of tests]

Note: This will renumber features 5+ to 6+
```

### 4. Confirm Before Editing

**Critical:** Always get explicit confirmation before making changes.

Ask: "Should I apply these changes to docs/features.md?"

Wait for affirmative response before editing.

### 5. Apply Changes

Use the Edit tool to update `docs/features.md`:
- Make the confirmed changes
- Update the "Last Updated" date
- Adjust feature numbers if needed
- Update dependencies if affected
- Update the feature count in header

### 6. Update Progress Log

Add a note to `docs/progress.md`:
```markdown
## Revision: [Brief Description]

**Date:** [DATE]

### Changes Made

- [What was changed and why]
- [Another change]

### Reason

[Brief explanation of what was learned during development]
```

## Types of Revisions

### Adding Tests
- Add new checkbox items to existing feature
- Common when edge cases are discovered

### Splitting Features
- Create new feature from subset of tests
- Renumber subsequent features
- Update dependencies pointing to old numbers

### Removing Features
- Mark as removed or delete entirely
- Update dependencies
- Renumber if deleting

### Changing Dependencies
- Update dependency list
- May require reordering features

### Updating Status
- Change from 🔴 to 🟡 or 🟢
- Only when tests are actually verified

### Adding Notes
- Implementation details discovered
- Gotchas for future reference
- Technical decisions made

## Safety Rules

1. **Always show changes before applying**
2. **Always get explicit confirmation**
3. **Never silently modify files**
4. **Preserve file structure and formatting**
5. **Update all affected sections** (count, dates, dependencies)

## Output

After applying changes:
- Confirm what was updated
- Show affected feature(s)
- Note any follow-up actions needed
