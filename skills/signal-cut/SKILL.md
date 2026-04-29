---
name: signal-cut
description: Reduce scope to the smallest milestone that produces real delivery signal. Use when work is too broad, MVP scope is unclear, priorities are drifting, or the user asks what to keep, defer, freeze, or remove.
---

# Signal Cut

Use this skill to protect milestone signal by removing work that does not prove
the next meaningful outcome.

## Workflow

1. Name the signal:
   - What external proof should exist after this milestone?
   - Who can observe it?
   - What decision does it unlock?
2. Inventory the current scope:
   - Features, integrations, docs, tests, polish, migration work, and operations.
3. Classify every meaningful item:
   - `Keep`: required for the signal.
   - `Defer`: useful later, not needed now.
   - `Freeze`: stop expanding; preserve current behavior.
   - `Remove`: actively distracts, duplicates, or increases risk.
4. Identify the tracer:
   - The thinnest coherent path that proves the signal.
5. State the milestone contract:
   - Acceptance criteria.
   - Explicit non-goals.
   - Risks accepted for this milestone.
   - Revisit triggers for deferred work.

## Classification Table

```markdown
| Item | Decision | Reason | Revisit trigger |
| --- | --- | --- | --- |
| <scope item> | Keep/Defer/Freeze/Remove | <why it affects signal> | <when to reconsider> |
```

## Guardrails

- Do not cut the core signal just to make the list shorter.
- Do not keep work because it is elegant, interesting, or already started.
- Do not defer verification or rollback if failure would be expensive.
- Do not turn a reduction pass into a redesign.

## Output

- `Signal`
- `Scope decisions`
- `Tracer`
- `Milestone contract`
- `Deferred work`
- `Risks`
