---
name: zero-tech-debt
description: Rework an existing change toward the intended final UX and architecture, deleting compatibility cruft, unused modes, stale fallbacks, and accidental complexity. Use when the user asks for zero tech debt, a clean end-state refactor, or to rebuild a patch as if it had been designed correctly from day one.
---

# Zero Tech Debt

Use this skill when a change should be reshaped from the intended end state
instead of preserved as the historical path that produced the current patch.
The goal is not broad cleanup; it is to make the final product surface and
architecture feel like they were designed that way from day one.

## Workflow

1. State the intended end state:
   - Describe the final UX, API, command, or architecture in one or two
     sentences.
   - Name the product intent, not the migration history.
2. Search for real callers before preserving compatibility:
   - Check imports, routes, tests, docs, command references, persisted state,
     feature flags, and runtime entrypoints relevant to the change.
   - If a mode, prop, wrapper, route alias, fallback, adapter, or branch has no
     current caller, delete it.
   - If dynamic usage is plausible, identify the exact verification needed
     before deletion.
3. Reshape around the final product surface:
   - Prefer one clear component, command, flow, or module over mode flags and
     compatibility branches.
   - Split only when it creates an obvious boundary such as state, layout,
     controls, domain commands, persistence, or permissions.
4. Move shared rules to one place:
   - Feature flags, permissions, route gating, URL state, validation,
     persistence rules, and command naming should not be duplicated across
     pages or hidden in view components.
5. Delete accidental complexity:
   - Remove unused wrappers, shims, bridge names, fallback behavior, redundant
     tests, and documentation that describe the old path rather than the final
     behavior.
   - Do not improve dead compatibility paths. Delete them when evidence says
     they are unused.
6. Verify the intended flow:
   - Test the new behavior and any deleted assumptions that affect navigation,
     permissions, persisted state, public APIs, or user-visible workflows.

## Guardrails

- Optimize for the code that should exist, not the smallest diff from the old
  shape.
- Keep the refactor scoped to what makes the final shape coherent.
- Do not invent a generic framework for one feature.
- Do not delete public API, persisted state, or compatibility behavior from
  static evidence alone when external callers are plausible.
- Prefer names that describe product intent over implementation history.
- Preserve behavior only when there is a real caller, external contract, or
  explicit product requirement.

## Output

- `Intended end state`
- `Caller evidence`
- `Deleted compatibility`
- `Final shape`
- `Verification`
- `Residual risk`
