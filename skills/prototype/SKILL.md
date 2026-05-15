---
name: prototype
description: Build throwaway prototypes that answer a specific product, UI, state-model, API, or workflow question before production implementation. Use when the user asks to prototype, try variants, explore a UI direction, sanity-check logic, make something playable, or test whether an idea feels right.
---

# Prototype

Use this skill when the goal is learning, not shipping. A prototype should
answer one question quickly, make the answer observable, and then be deleted or
absorbed into production work.

## Choose The Prototype Type

Pick one type before editing code:

- `logic`: business rules, state machines, reducers, workflows, APIs, data
  shape, command behavior, or edge-case exploration. Read
  [logic.md](references/logic.md).
- `ui`: page, component, dashboard, app flow, interaction model, or visual
  direction exploration. Read [ui.md](references/ui.md).

If both apply, separate them unless one clearly blocks the other. For example,
prototype the state model first when UI variants depend on unresolved states.

## Workflow

1. State the question:
   - What decision should the prototype unlock?
   - What would count as a useful answer?
2. Locate it near the real context:
   - Prefer a nearby route, module, package, or `.context/` note over an
     unrelated demo area.
   - Name files and routes with `prototype` so they cannot be mistaken for
     production surfaces.
3. Keep the implementation temporary:
   - In-memory state by default.
   - Real project runtime and component conventions.
   - No new package, framework, database, or service unless the question
     specifically requires it.
4. Make the state visible:
   - Logic prototypes should print current state after each action.
   - UI prototypes should expose variant identity and representative states.
5. Provide one way to run or view it:
   - Existing package script, existing dev server route, or a clear command.
6. Capture the answer:
   - Record the question, what the prototype showed, and the decision it
     supports in a nearby note, issue, ADR, commit message, or final response.
7. Clean up deliberately:
   - Delete losing variants and throwaway shells.
   - Fold validated logic or UI decisions into production code with normal
     quality, tests, and error handling when implementation begins.

## Guardrails

- Do not let prototype code silently become production code.
- Do not add broad abstractions, persistence, or hardening before the question
  has been answered.
- Do not build several variants that differ only by color, copy, or spacing.
- Do not bypass existing design-system, routing, or runtime conventions unless
  the point is to challenge them explicitly.
- Do not skip verification that the prototype actually runs or renders.
- Do not leave prototype routes, scripts, or switchers merged without a cleanup
  decision.

## Output

- `Prototype type`
- `Question`
- `Artifact path or URL`
- `How to run`
- `What it tests`
- `Cleanup plan`
