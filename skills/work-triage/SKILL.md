---
name: work-triage
description: Triage incoming issues, bugs, feature requests, or work items through a tracker-neutral state machine. Use when deciding whether work needs info, is ready for an agent, needs a human, is out of scope, or should be closed.
---

# Work Triage

Use this skill to turn vague incoming work into an actionable state.

## States

- `needs-triage`: requires maintainer evaluation.
- `needs-info`: blocked on reporter/user details.
- `ready-for-agent`: specified enough for an agent to execute.
- `ready-for-human`: needs judgment, access, or authority an agent lacks.
- `out-of-scope`: should not be actioned now.
- `done/closed`: already addressed or no longer relevant.

## Categories

- `bug`: broken expected behavior.
- `enhancement`: new or improved behavior.
- `question`: asks for explanation.
- `cleanup`: residue, refactor, docs, or maintenance.
- `risk`: security, data, permission, or reliability concern.

## Workflow

1. Read the item:
   - Body, comments, labels, linked docs, prior notes.
2. Gather repo context:
   - Relevant code, tests, docs, domain terms, ADRs.
3. Recommend category and state:
   - Explain evidence.
   - Identify missing info.
4. For bugs:
   - Attempt a quick reproduction or identify exact missing repro info.
5. Prepare the next artifact:
   - `needs-info`: specific questions.
   - `ready-for-agent`: agent-ready brief.
   - `ready-for-human`: why human judgment is needed.
   - `out-of-scope`: reason and revisit trigger if any.

## Agent-Ready Brief

```markdown
## Goal

## Context

## Scope

## Acceptance Criteria

## Verification

## Known Risks
```

## Guardrails

- Do not ask vague "please provide more info" questions.
- Do not mark work ready for agent if decisions, access, or repro are missing.
- Do not change tracker labels unless the user asks or repo convention is clear.
- Preserve prior triage notes; do not re-ask resolved questions.

## Output

- `Recommended category`
- `Recommended state`
- `Reasoning`
- `Missing information`
- `Next artifact`
