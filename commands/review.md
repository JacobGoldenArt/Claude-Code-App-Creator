---
name: review
description: Review and refine the feature list until it feels complete
argument-hint: ""
allowed-tools: ["Read", "Write", "Glob", "Grep", "TodoWrite", "AskUserQuestion"]
---

# Review: Refine Until Complete

Iterate with the user on the feature list until they look at it and think "yes, that's my app."

## Prerequisites

This step requires a completed `/app-creator:breakdown` session. Look for:
- Complete feature breakdown with tests
- All features have 8-15 binary tests

If no prior breakdown exists, inform the user to run `/app-creator:breakdown` first.

## Review Process

### 1. Present the Full Picture

Display a summary view of all features:
- Feature count and names
- Dependency map (what depends on what)
- Estimated implementation order

Ask: "Does this capture your app?"

### 2. Gather Feedback

Listen for these types of feedback:

**Adding Features:**
- "I forgot about X"
- "We also need Y"

**Removing Features:**
- "Actually, we don't need X"
- "That's more of a v2 thing"

**Modifying Features:**
- "X should also do Y"
- "The tests for X are missing Z"

**Splitting Features:**
- "X feels too big"
- "Can we break X into smaller pieces?"

**Merging Features:**
- "X and Y are really the same thing"

### 3. Apply Changes

For each piece of feedback:
1. Understand the desired change
2. Propose the specific modification
3. Confirm before applying
4. Update dependencies if affected
5. Re-order if necessary

### 4. Iterate

After each round of changes:
- Present updated summary
- Ask if more changes needed
- Continue until user confirms completion

## Completion Criteria

The review is complete when the user:
- Confirms the feature list is accurate
- Agrees with the implementation order
- Has no more changes to make
- Says something like "yes, that's my app"

## Common Refinements

### Feature Too Large
Split into smaller features:
- Identify distinct sub-functionalities
- Create separate features for each
- Update dependencies accordingly

### Missing Edge Cases
Add tests for:
- Empty states
- Error conditions
- Boundary values
- Concurrent operations

### Unclear Tests
Rewrite to be more specific:
- Before: "Works correctly"
- After: "Displays success message after save"

### Dependency Issues
Fix ordering problems:
- Feature depends on something that comes later
- Circular dependencies (need to refactor)
- Missing intermediate features

## Output

Final confirmed feature list:
- All features with complete tests
- Accurate dependency ordering
- User-approved and ready for implementation

## Transition

Once the user confirms the feature list is complete:
- Inform them to run `/app-creator:finalize` to generate the documentation files
- Remind them this is their last chance to make changes before files are created

## Quality Check

Before completing review:
- [ ] User explicitly confirmed the list is complete
- [ ] All features are small enough for one session
- [ ] Dependencies are logical and achievable
- [ ] No circular dependencies
- [ ] Implementation order makes sense
- [ ] Nice-to-haves are clearly marked (if any)
