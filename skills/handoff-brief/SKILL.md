---
name: handoff-brief
description: Package work so a future session, teammate, or agent can continue safely with context, changed files, verification artifacts, risks, and next actions. Use before delegation, after partial work, or when closing a task that may resume later.
---

# Handoff Brief

Use this skill when continuity matters.

## Workflow

1. Capture task state:
   - Original goal.
   - Current status.
   - What changed.
   - What remains.
2. Record context:
   - Important files.
   - Decisions made.
   - Assumptions.
   - Constraints.
3. Record verification:
   - Commands run.
   - Results.
   - Manual checks.
   - Checks not run and why.
4. Identify risk:
   - Unverified behavior.
   - Open decisions.
   - Known edge cases.
   - Rollback notes.
5. Make next action executable:
   - One or more worker-ready prompts or steps.
   - Include exact paths and expected outputs.

## Brief Format

```markdown
## Goal

## Current state

## Files and context

## Verification

## Risks

## Next actions
```

## Guardrails

- Do not write a vague status update.
- Do not omit failed or skipped verification.
- Do not include irrelevant implementation diary.
- Do not assume the next agent has hidden context.

## Output

- `Handoff brief`
- `Worker-ready next action`
