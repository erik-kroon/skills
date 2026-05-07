---
name: module-deepening
description: Find architecture deepening opportunities that create simpler interfaces, better seams, stronger locality, and more testable modules. Use when code feels shallow, tangled, over-extracted, hard to test, or difficult for agents to navigate.
---

# Module Deepening

Use this skill to surface architectural friction and propose deepening
opportunities: refactors that turn shallow modules into deeper ones. The aim is
testability, locality, leverage, and code that future agents can navigate
without bouncing through accidental structure.

## Vocabulary

Use these terms exactly in every suggestion.

- `Module`: anything with an interface and an implementation: function, class,
  package, feature slice, or tier-spanning unit.
- `Interface`: everything a caller must know to use the module correctly:
  types, invariants, ordering, error modes, required config, performance
  characteristics, and lifecycle constraints.
- `Implementation`: the code inside the module.
- `Depth`: leverage at the interface. A deep module puts a lot of behavior
  behind a small interface. A shallow module has an interface nearly as complex
  as its implementation.
- `Seam`: where an interface lives; a place behavior can be altered without
  editing in that place.
- `Adapter`: a concrete implementation that satisfies an interface at a seam.
- `Leverage`: what callers get from depth.
- `Locality`: what maintainers get from depth: change, bugs, knowledge, and
  verification concentrated in one place.

Do not substitute `component`, `service`, `API`, or `boundary` when the concept
is really a module, interface, or seam.

## Principles

- Depth is a property of the interface, not the implementation. A module may
  have internal seams without exposing them to callers.
- The deletion test: if deleting the module makes complexity vanish, it was
  probably a pass-through. If complexity reappears across callers, it was
  earning its keep.
- The interface is the test surface. If tests need to reach past it, the module
  shape is probably wrong.
- One adapter means a hypothetical seam. Two adapters, a useful test adapter, or
  real operational variation can justify a seam.
- Domain language names good modules. Prefer terms from `CONTEXT.md`,
  `CONTEXT-MAP.md`, docs, ADRs, and user language over generic technical names.

## Workflow

1. Read domain language and decisions:
   - `CONTEXT.md`, `CONTEXT-MAP.md`, relevant docs, ADRs, tests, callers, and
     nearby modules.
   - If context docs or ADRs do not exist, proceed silently.
2. Explore organically and note friction:
   - Where does understanding require bouncing across many files?
   - Which modules are pass-through or shallow?
   - Where have pure functions been extracted only for testability while bugs
     still live in how callers assemble them?
   - Where are tests forced through awkward private internals?
   - Where does one concept have several names?
   - Where do tightly-coupled modules leak across their seams?
   - Which behavior is hard to test through the current interface?
3. Apply the deletion test:
   - Ask whether deleting the module concentrates complexity or just moves it.
   - Treat "complexity vanishes" as a deletion or consolidation signal.
   - Treat "complexity spreads across N callers" as a deepening signal.
4. Present deepening candidates before proposing interfaces:
   - Do not implement yet unless asked.
   - Do not design the new interface yet; first ask which candidate to explore.
   - Explain benefits in terms of locality, leverage, testability, deletion,
     and simpler callers.
   - Call out ADR conflicts only when real friction makes the ADR worth
     revisiting.
5. If the user selects a candidate, shape the refactor:
   - Constraints the new interface must satisfy.
   - Dependencies behind the seam and whether adapters are real or hypothetical.
   - Characterization tests that should survive the change.
   - Migration sequence and rollback-safe slices.
   - Alternative interface sketches when the design space is not obvious.
6. Record durable decisions:
   - If a chosen module name introduces a real domain concept, suggest updating
     `CONTEXT.md`.
   - If the user rejects a candidate for a durable reason future reviewers would
     rediscover, suggest recording an ADR.

## Candidate Format

```markdown
1. **<candidate title>**
   - Files: `<paths/modules>`
   - Problem: `<why the current architecture causes friction>`
   - Deepening move: `<plain English change, not an interface proposal yet>`
   - Benefits: `<locality, leverage, testability, simpler callers>`
   - ADR/context notes: `<conflict, missing term, or none>`
   - Verification path: `<tests, characterization, or inspection needed>`
```

## Guardrails

- Do not propose generic layering.
- Do not invent interfaces before identifying real second use or test value.
- Do not contradict ADRs silently; call out real conflicts.
- Do not turn architecture review into broad implementation unless requested.
- Do not list theoretical refactors that lack observed friction.
- Do not rename domain concepts casually; names are part of the interface.

## Output

- `Domain language`
- `Friction map`
- `Deepening candidates`
- `Recommended candidate`
- `Verification path`
- `Question: Which candidate should I explore?`
