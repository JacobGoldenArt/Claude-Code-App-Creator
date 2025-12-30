---
name: analyze
description: Solidify the app concept, identify gaps, and ask follow-up questions
argument-hint: ""
allowed-tools: ["Read", "Write", "Glob", "Grep", "TodoWrite", "AskUserQuestion"]
---

# Analyze: Solidify the App Concept

Review the brainstorming session and transform scattered ideas into a coherent, buildable app concept.

## Prerequisites

This step requires a completed `/app-creator:start` session. Look for:
- Recent conversation context with app brainstorming
- Or existing notes/summary from the start session

If no prior context exists, inform the user to run `/app-creator:start` first.

## Analysis Process

### 1. Synthesize Ideas

Review everything discussed and organize into coherent feature areas:
- Group related functionality together
- Identify the core user journey
- Distinguish must-have from nice-to-have

### 2. Find Logic Holes

Look critically for gaps or issues:
- What happens when things go wrong?
- How does data persist between sessions?
- Are there conflicting requirements?
- What implicit features are missing? (auth, error handling, loading states)
- Does the user flow have dead ends?

### 3. Ask Follow-Up Questions

For any gaps or ambiguities identified, ask targeted follow-up questions:
- Present 2-3 questions at a time
- Offer concrete options when possible
- Explain why the question matters

### 4. Map the User Journey

Walk through the app from a user's perspective:
- First-time user experience
- Returning user experience
- Key workflows from start to finish
- Edge cases and error scenarios

### 5. Define Feature Boundaries

Create a preliminary feature list:
- Each feature is a cohesive unit
- Features are small enough for one coding session
- Clear boundaries between features
- Identify dependencies between features

### 6. Define the Initial Tech Stack

Determine the tech stack for the app:
- Frontend
- Backend
- Database
- ORM
- External SDKs and APIs that will be used
- list of libraries/dependencies/requirements that will be needed


## Output

Create a structured summary including:

1. **App Overview** - 2-3 sentence description
2. **Primary User** - Who this is for
3. **Core Features** - Numbered list of main features (high-level)
4. **User Journey** - How users move through the app
5. **Tech Stack** - Confirmed or recommended technologies
6. **Open Questions** - Any remaining uncertainties
7. **Dependencies** - Which features depend on others

Present this to the user for confirmation before proceeding.

## Transition

Once the user confirms the analysis is accurate:
- Inform them to run `/app-creator:breakdown` to decompose features into testable items
- Note any remaining questions to address during breakdown

## Common Issues to Catch

- **Scope creep** - Features that belong in v2, not v1
- **Missing authentication** - Most apps need it but users forget
- **No error handling** - What happens when network fails?
- **Data persistence** - Where does data live?
- **Empty states** - What do users see before any data exists?
- **Loading states** - What happens during async operations?
