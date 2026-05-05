---
name: module-deepening
description: Find architecture deepening opportunities that create simpler interfaces, better seams, stronger locality, and more testable modules. Use when code feels shallow, tangled, over-extracted, hard to test, or difficult for agents to navigate.
---

# Module Deepening

Use this skill to find structural improvements without jumping straight to a
rewrite.

## Vocabulary

- `Module`: any unit with an interface and implementation.
- `Interface`: what callers must know to use the module.
- `Implementation`: the hidden work behind the interface.
- `Seam`: the place behavior can be varied or tested.
- `Depth`: useful behavior hidden behind a small interface.
- `Leverage`: what callers get from depth.
- `Locality`: related knowledge and change concentrated in one place.

## Workflow

1. Read domain language and decisions:
   - `CONTEXT.md`, ADRs, relevant docs, tests, and callers.
2. Explore friction:
   - Where does understanding require bouncing across many files?
   - Which modules are pass-through or shallow?
   - Where are tests forced through awkward private seams?
   - Where does one concept have several names?
3. Apply the deletion test:
   - If deleting a module makes complexity vanish, it may be accidental.
   - If deleting it spreads complexity across callers, it may be earning its keep.
   - If there is only one adapter, treat the seam as hypothetical until a real second use, test value, or operational variation justifies it.
4. Present candidates:
   - Do not implement yet unless asked.
   - Make benefits concrete: locality, leverage, testability, deletion, or simpler callers.
   - Call out ADR conflicts only when the friction is real enough to warrant revisiting the decision.
5. If selected, shape the refactor:
   - Interface.
   - Migration sequence.
   - Characterization tests.
   - Rollback-safe slices.

## Candidate Format

```markdown
| Candidate | Files | Current friction | Deepening move | Verification |
| --- | --- | --- | --- | --- |
```

## Guardrails

- Do not propose generic layering.
- Do not invent interfaces before identifying real second use or test value.
- Do not contradict ADRs silently; call out real conflicts.
- Do not turn architecture review into broad implementation unless requested.

## Output

- `Domain language`
- `Friction map`
- `Deepening candidates`
- `Recommended candidate`
- `Verification path`
