---
name: breakdown
description: Break each feature into detailed, binary testable items
argument-hint: ""
allowed-tools: ["Read", "Write", "Glob", "Grep", "TodoWrite", "AskUserQuestion"]
---

# Breakdown: Feature Decomposition

Transform each feature from the analysis into detailed, binary testable specifications.

## Prerequisites

This step requires a completed `/app-creator:analyze` session. Look for:
- Feature list from the analysis phase
- Clear app concept and user journey

If no prior analysis exists, inform the user to run `/app-creator:analyze` first.

## Load Resources

Read the example features for reference:
- `app-creator/skills/app-discovery/references/example-features.md`

These examples show the level of detail and test quality to aim for.

## Breakdown Process

For each feature identified in the analysis:

### 1. Write the Description

Describe what the user experiences when this feature works:
- Focus on user perspective, not implementation
- Be specific about what they can do
- One clear sentence

### 2. Identify Dependencies

Determine what must exist before this feature:
- `None` for foundational features
- List specific feature numbers for dependent features
- This determines implementation order

### 3. Write Binary Tests

Create 8-15 specific, observable tests:

**Test Categories:**
- **Visibility** - Elements are present and visible
- **Interaction** - User actions produce expected results
- **State changes** - Data updates correctly
- **Edge cases** - Unusual inputs handled gracefully
- **Error states** - Failures communicated clearly

**Test Quality:**
- Each test has a clear pass/fail outcome
- Focus on observable behaviors
- Avoid vague criteria ("works well", "is fast")
- Include both happy path and edge cases

### 4. Add Notes

Include any implementation considerations:
- Technical approaches to consider
- Potential gotchas
- Accessibility requirements
- Performance considerations

## Feature Template

Use this structure for each feature:

```markdown
### N. [Feature Name]

**Status:** 🔴 Not Started

**Description:** [What the user experiences when this feature works]

**Dependencies:** None | [Feature numbers]

**Tests:**
- [ ] [Specific, observable outcome]
- [ ] [Another specific, observable outcome]
- [ ] [Edge case]
- [ ] [Error state]

**Notes:** [Implementation considerations]
```

## Ordering Features

Arrange features by dependency order:
1. Foundation features (no dependencies) first
2. Features that depend on #1 next
3. Continue building up the dependency tree
4. Nice-to-have features at the end

## Output

Present the complete breakdown to the user:
- All features with full test specifications
- Clear dependency ordering
- Total feature count

Ask if any features need adjustment:
- Too large? (Should be split)
- Missing tests?
- Wrong dependencies?

## Transition

Once the user is satisfied with the breakdown:
- Inform them to run `/app-creator:review` for final refinement
- Note: Tests can still be adjusted in review phase

## Quality Checklist

Before completing breakdown:
- [ ] Each feature has 8-15 tests
- [ ] All tests are binary (clear pass/fail)
- [ ] No vague criteria
- [ ] Dependencies are accurate
- [ ] Features are ordered correctly
- [ ] Edge cases are covered
- [ ] Error states are included
