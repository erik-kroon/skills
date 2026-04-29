---
name: contract-review
description: Review code, diffs, and boundaries with findings-first output focused on correctness, data safety, trust boundaries, state transitions, permissions, and verification gaps. Use when the user asks for review or risk assessment.
---

# Contract Review

Use this skill for review, not implementation.

## Workflow

1. Confirm scope:
   - Diff, branch, files, PR, issue, or explicit paths.
2. Read contracts:
   - Public interfaces, schemas, routes, state machines, permissions, tests, and callers.
3. Apply the taxonomy:
   - `data-safety`
   - `trust-boundary`
   - `permission-regression`
   - `state-transition`
   - `enum/completeness`
   - `type/coercion`
   - `time/window`
   - `i18n/locale`
   - `accessibility`
   - `verification-gap`
4. Report findings first:
   - Order by severity.
   - Include file references and concrete failure modes.
5. If no findings:
   - Say so directly.
   - Name residual risk and test gaps.

## Finding Format

```markdown
### <severity>: <title>

- Location: `<file>`
- Risk: <what can go wrong>
- Evidence: <why this is plausible>
- Fix direction: <minimal safe fix>
```

## Guardrails

- Do not pad review with compliments.
- Do not scan unrelated areas unless the changed contract requires it.
- Do not recommend rewrites when a boundary fix is enough.
- Do not treat missing tests as the only finding if behavior is visibly wrong.

## Output

- `Findings`
- `Taxonomy coverage`
- `Verification gaps`
- `Open questions`
- `Residual risk`
