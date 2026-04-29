---
name: product-brief
description: Turn conversation context, codebase findings, and product intent into a PRD-style brief without assuming a specific issue tracker. Use when the user wants a PRD, product brief, feature spec, or implementation-ready product artifact.
---

# Product Brief

Use this skill to freeze fuzzy product intent into a durable artifact.

## Workflow

1. Gather context:
   - Current conversation.
   - Existing docs.
   - Similar code paths.
   - Domain vocabulary.
   - Known constraints and non-goals.
2. Identify product shape:
   - Problem.
   - Users or actors.
   - Desired behavior.
   - Success signal.
   - Out of scope.
3. Identify implementation shape:
   - Modules or surfaces likely touched.
   - Interfaces likely affected.
   - Testing decisions.
   - Risks and open decisions.
4. Write the brief:
   - Keep it stable; avoid file paths that will quickly rot unless needed.
   - Use domain language.
   - Mark uncertain claims clearly.
5. Choose publishing target:
   - Markdown document.
   - Issue body.
   - Worker handoff.
   - Tracker-specific payload only when requested.

## Brief Template

```markdown
## Problem

## Users / Actors

## Desired Outcome

## User Stories

## Functional Requirements

## Implementation Notes

## Testing Decisions

## Out of Scope

## Open Questions
```

## Guardrails

- Do not interview when the conversation already contains enough context.
- Do not pretend uncertain implementation details are decided.
- Do not publish to a tracker unless asked.
- Do not include brittle code snippets in a durable PRD.

## Output

- `Product brief`
- `Open questions`
- `Suggested next artifact`
