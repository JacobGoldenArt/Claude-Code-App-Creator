---
name: start
description: Begin the app discovery process with a brainstorming interview
argument-hint: "[optional: brief app idea]"
allowed-tools: ["Read", "Glob", "Grep", "TodoWrite", "AskUserQuestion"]
---

# Start: Brainstorming Interview

Begin the app discovery process by interviewing the user about their app idea.

## Prerequisites

Check if a discovery session is already in progress by looking for existing files:
- `docs/features.md`
- `CLAUDE.md`

If these exist, inform the user and ask if they want to start fresh or continue with `/app-creator:analyze`.

## Interview Approach

Conduct a **conversational, low-pressure interview**:

1. **Start broad** - Understand the big picture first
2. **Ask 2-3 questions at a time** - Never overwhelming questionnaires
3. **Follow the user's energy** - Explore what excites them
4. **Keep it light** - Ideas can change, and that's fine
5. **Draw out hidden details** - Ask about things they might not mention

## Key Areas to Explore

### The Vision
- What problem does this app solve?
- Who is the primary user?
- What does success look like?

### Core Functionality
- What are the 3-5 most important things a user can do?
- Walk me through a typical session with this app
- What would frustrate a user most if it didn't work?

### Inspiration & Preferences
- Any existing apps that inspire this one?
- Strong preferences on tech stack?
- Any features you definitely don't want?

### Scope
- What's the simplest version that would still be useful?
- Any must-have vs nice-to-have distinctions?

## Interview Flow

1. If user provided an app idea in the command, acknowledge it and ask clarifying questions
2. If no idea provided, ask what they want to build
3. Ask follow-up questions in batches of 2-3
4. Reflect back understanding periodically
5. Note when user says "obviously" or "of course" - these hide assumptions
6. Continue until a clear picture emerges

## Session Output

When the interview feels complete (user has shared enough to understand the vision):

1. Summarize the app concept in 2-3 paragraphs
2. List the key features discussed (high-level, not detailed yet)
3. Note any tech stack preferences mentioned
4. Identify any open questions or decision points
5. Save this summary for the next step

Inform the user to run `/app-creator:analyze` to continue to the next step.

## Tips

- Treat the user like a client who hired you as a developer
- This is brainstorming - not everything needs to be perfect
- Capture the "vibe" even if specifics are fuzzy
- Flag uncertainties rather than forcing decisions
- End when you have enough to work with, not when every detail is known
