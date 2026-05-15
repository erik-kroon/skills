---
name: handoff
description: Create a compact repo-local handoff document for another agent or future session to continue work. Use when the user asks to hand off, summarize current work for another workspace, preserve session state, or prepare a continuation brief.
---

# Handoff

Use this skill to preserve continuity without turning the handoff into a second
copy of the repo.

## Workflow

1. Define the next reader:
   - Another agent in this repo.
   - A future session after context compaction.
   - A human reviewer who needs current state and next steps.
2. Choose the artifact path:
   - Default to `.context/handoff-<YYYYMMDD-HHMM>-<slug>.md`.
   - Use a user-provided path only when requested.
   - Keep the artifact repo-local and ignored when possible.
3. Read before writing:
   - If updating an existing handoff, read it first and preserve still-current
     details.
   - If creating a new one, inspect current git status, recent diffs, relevant
     notes, open commands, and blocking context.
4. Write only continuation-critical facts:
   - Objective and current status.
   - Files changed or relevant paths.
   - Decisions made.
   - Commands run and verification results.
   - Blockers, risks, and exact next steps.
   - Skills likely useful next.
5. Reference durable artifacts instead of duplicating them:
   - Link to PRDs, ADRs, issues, commits, diffs, notes, screenshots, and logs.
   - Summarize only what the next reader needs to restart safely.
6. Verify the handoff:
   - Paths exist or are clearly marked as intended future paths.
   - No stale task, command, or branch information remains.
   - The next step is concrete enough to execute.

## Handoff Template

```markdown
# Handoff: <short title>

## Objective

## Current Status

## Important Context

## Files And Artifacts

## Decisions

## Verification

## Blockers And Risks

## Suggested Next Skills

## Next Steps
```

## Guardrails

- Do not duplicate long specs, logs, or diffs already stored elsewhere.
- Do not hide uncertainty; mark assumptions and unresolved decisions directly.
- Do not write to `/tmp` or an undiscoverable location unless the user asks.
- Do not leave out dirty worktree state when it affects continuation.
- Do not claim verification that was not run.

## Output

- `Handoff path`
- `Status captured`
- `Next steps`
