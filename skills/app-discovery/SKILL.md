---
name: App Discovery
description: This skill should be used when the user asks to "discover an app idea", "clarify app requirements", "break down features", "create a feature list", "define app scope", "interview about an app", "decompose features into tests", or mentions app planning, feature decomposition, or preflight discovery sessions.
version: 0.1.0
---

# App Discovery Methodology

A structured approach for clarifying app ideas and decomposing them into atomic, testable features before writing any code.

## Purpose

Transform vague app ideas into actionable, well-defined feature lists through:
1. Conversational interviews to understand the vision
2. Analytical review to identify gaps and solidify concepts
3. Systematic breakdown into binary testable items
4. Iterative refinement until the spec feels complete

## Core Principles

### Preflight Only

This is a discovery process, not implementation. No code writing occurs. Focus entirely on understanding and documentation.

### Atomic Features

Each feature must be:
- A cohesive unit of functionality
- Independently testable
- Small enough to complete in one focused coding session
- Clear about what the user experiences when it works

### Binary Tests

Every feature includes specific, observable tests with clear pass/fail outcomes:
- Avoid vague criteria like "works well" or "is fast"
- Focus on observable behaviors: "button is visible", "text clears after submit"
- Include edge cases and error states
- Tests become the definition of "done"

### Dependency Mapping

Identify which features must exist before others. This determines implementation order and prevents blocked work.

## The Five-Step Process

### Step 1: Start (Brainstorming Interview)

Conduct an easy, conversational interview to capture the app vision:

- Ask 2-3 questions at a time (not overwhelming questionnaires)
- Treat the user like a client who hired a developer
- Draw out details they might not think to mention
- Explore: what the app does, who uses it, key workflows, tech preferences
- Keep it light—ideas might change, and that's fine
- Goal: establish the "vibe" and high-level scope

**Key questions to explore:**
- What problem does this app solve?
- Who is the primary user?
- What are the 3-5 most important things a user can do?
- Any strong preferences on tech stack or approach?
- What existing apps inspire this one?

### Step 2: Analyze (Solidification)

Review the brainstorm output and solidify into something buildable:

- Synthesize scattered ideas into coherent feature areas
- Look for potential holes in logic or missing pieces
- Identify implicit features (auth, error handling, data persistence)
- Challenge assumptions with follow-up questions
- Map out the user journey from start to finish
- Goal: a clear, coherent app concept with no major gaps

**Analysis questions:**
- What happens when X goes wrong?
- How does data persist between sessions?
- What's the minimum viable version?
- Are there conflicting requirements?

### Step 3: Breakdown (Feature Decomposition)

Transform each feature into detailed, testable specifications:

- Apply the feature template consistently
- Write 8-15 binary tests per feature
- Cover happy path, edge cases, and error states
- Identify dependencies between features
- Order features by dependency (foundations first)
- Goal: every feature has clear acceptance criteria

Use the feature template from `references/templates.md`.

### Step 4: Review (Refinement)

Iterate with the user until the feature list feels complete:

- Present the full feature list for review
- Ask: "Does this capture your app?"
- Adjust based on feedback (add, remove, modify features)
- Verify test coverage is sufficient
- Confirm implementation order makes sense
- Goal: user looks at the list and thinks "yes, that's my app"

### Step 5: Finalize (Documentation)

Generate the final documentation files:

- `docs/features.md` - Complete feature list with tests
- `CLAUDE.md` - Project overview and tech stack
- `docs/progress.md` - Discovery session summary

Ensure the `docs/` directory exists before writing files.

Use templates from `references/templates.md`.

## Post-Discovery: Revise

After development begins, features may need updating based on learnings:

- Listen to what the user discovered during implementation
- Propose specific changes to features or tests
- Show diff-style preview of proposed changes
- Wait for confirmation before editing files
- Update status indicators as features complete

## Interview Techniques

### Conversational Flow

Keep interviews natural and productive:

- Start broad, then drill into specifics
- Follow the user's energy—explore what excites them
- Note when they say "obviously" or "of course"—these hide assumptions
- Ask "what else?" to surface forgotten requirements
- Reflect back understanding to confirm alignment

### Drawing Out Details

Uncover hidden requirements:

- "Walk me through a typical session with this app"
- "What would frustrate a user most if it didn't work?"
- "What's the simplest version that would still be useful?"
- "Are there any features you definitely don't want?"

### Handling Uncertainty

When the user isn't sure:

- Offer 2-3 concrete options to react to
- Suggest what similar apps do
- Flag it as a decision point for later
- Don't force premature decisions

## Writing Effective Tests

### Good Tests

```markdown
- [ ] Text area is visible at bottom of chat view
- [ ] Pressing Enter submits the message (when not shift+enter)
- [ ] Empty submissions are prevented (button disabled, enter ignored)
```

### Bad Tests

```markdown
- [ ] Input works correctly (too vague)
- [ ] User experience is good (not observable)
- [ ] Performance is acceptable (no clear threshold)
```

### Test Categories

Cover these aspects for each feature:
1. **Visibility** - Elements are present and visible
2. **Interaction** - User actions produce expected results
3. **State changes** - Data updates correctly
4. **Edge cases** - Unusual inputs handled gracefully
5. **Error states** - Failures communicated clearly

## Additional Resources

### Reference Files

For templates and detailed examples:
- **`references/templates.md`** - File templates (features.md, CLAUDE.md, progress.md)
- **`references/example-features.md`** - Well-defined feature examples

### Using Templates

When creating output files, load the appropriate template from `references/templates.md` and adapt it to the specific project.
