---
name: shape-contract
description: Turn ambiguous or cross-surface work into an implementation contract with scope posture, requirements, risk tier, decision gates, and verification level. Use before building when requirements, sequencing, or safety are unclear.
---

# Shape Contract

Use this skill when the task needs shaping before implementation.

## Workflow

1. Ground in the repo:
   - Read nearby code, tests, docs, and existing patterns before inventing structure.
2. Choose scope posture:
   - `expand`: add surface only when it materially improves signal.
   - `hold`: direction is right; details need confirmation.
   - `reduce`: scope/noise is outrunning milestone value.
3. Write requirements:
   - Use `R0`, `R1`, `R2` for concise requirements.
   - Include non-goals when they prevent drift.
4. Assign risk tier:
   - `R0`: trivial or docs-only.
   - `R1`: local behavior, easy rollback.
   - `R2`: cross-surface or user-visible behavior.
   - `R3`: data, auth, billing, migration, security, or hard rollback.
5. Set verification level:
   - `standard`: focused check is enough.
   - `heightened`: tests plus broader build/typecheck/manual check.
   - `critical`: explicit regression path and rollback notes.
6. Define decision gates:
   - Only list decisions that block safe implementation.
7. Breadboard workflows when UI and code affordances need wiring:
   - Use this for multi-step product flows, existing-system mapping, or shaped
     parts that must interact.
   - Identify `Places`: perceptual contexts where a user or caller has a
     bounded set of available actions.
   - Use the blocking test: if the user cannot interact with what is behind, it
     is a different place.
   - Separate UI affordances from code affordances.
   - Capture `Wires Out` for what an affordance triggers and `Returns To` for
     where data/control comes back.
   - Mark tentative affordances with `?` and system boundaries explicitly.
8. Create execution slices:
   - 3 to 7 checkable steps.
   - Keep slices rollback-safe.

## Breadboard Format

Use this only when it clarifies the contract.

```markdown
### Places

| ID | Place | Description |
| --- | --- | --- |
| P1 | <place> | <bounded interaction context> |

### UI Affordances

| ID | Place | Affordance | Control | Wires Out | Returns To |
| --- | --- | --- | --- | --- | --- |
| U1 | P1 | <user-visible action/state> | <click/type/view/etc> | <target> | <target> |

### Code Affordances

| ID | Place/System | Affordance | Input | Wires Out | Returns To |
| --- | --- | --- | --- | --- | --- |
| N1 | <system> | <loader/action/job/API> | <data> | <target> | <target> |
```

## Guardrails

- Do not over-plan a one-file deterministic fix.
- Do not ask questions the repo can answer.
- Do not proceed when an unresolved decision could invalidate the work.
- Do not create abstractions before seeing existing patterns.
- Do not breadboard simple one-step work; use it only when wiring is the risk.

## Output

- `Scope posture`
- `Requirements`
- `Risk tier`
- `Verification level`
- `Decision gates`
- `Breadboard` when useful
- `Execution slices`
- `Open questions`
