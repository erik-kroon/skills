---
name: interface-craft
description: Improve interface quality through mode-based design operations: critique, audit, polish, clarify, harden, adapt, distill, amplify, extract, and motion craft. Use for UI/UX/frontend work where taste, usability, resilience, or design-system quality matters.
---

# Interface Craft

Use this skill for interface work where the goal is not merely "make it work"
but make it clear, durable, and intentionally designed.

## Choose A Mode

Pick one primary mode from the user request. If the request is broad, start
with `critique` or `audit` before changing code.

| Mode | Use when | Reference |
| --- | --- | --- |
| `critique` | Judge whether the design works as an experience | [critique.md](references/critique.md) |
| `audit` | Produce prioritized findings across a11y, performance, theming, responsive behavior, and anti-patterns | [audit.md](references/audit.md) |
| `polish` | Finish a mostly complete interface before shipping | [polish.md](references/polish.md) |
| `clarify` | Improve labels, empty states, errors, instructions, and UX copy | [clarify.md](references/clarify.md) |
| `harden` | Make the interface resilient to edge cases, long text, loading, errors, i18n, and offline states | [harden.md](references/harden.md) |
| `adapt` | Make the design work across screen sizes, input methods, or contexts | [adapt.md](references/adapt.md) |
| `distill` | Remove complexity and reduce the interface to what matters | [distill.md](references/distill.md) |
| `amplify` | Adjust expression: bolder, quieter, more colorful, or more delightful | [amplify.md](references/amplify.md) |
| `extract` | Pull repeated patterns into reusable components, tokens, or design-system guidance | [extract.md](references/extract.md) |
| `motion` | Decide whether and how motion should exist | [motion.md](references/motion.md) |

## Shared Craft Baseline

Always apply these principles:

1. Identify the user's job before changing visuals.
2. Preserve existing design-system conventions unless they are the problem.
3. Avoid generic AI tells: identical card grids, cyan/purple glow palettes, gradient text, decorative glassmorphism, oversized hero metrics, and generic fonts.
4. Make hierarchy obvious: primary action, scan path, grouping, and density.
5. Make states complete: default, hover, focus, active, disabled, loading, empty, error, success.
6. Verify across at least one narrow and one wide layout when possible.
7. Respect accessibility: labels, contrast, focus, keyboard path, reduced motion, touch targets.
8. Prefer fewer high-impact changes over decorative churn.

## Motion Decision Gate

Before adding motion:

1. How often will users see it?
2. What purpose does it serve?
3. Can it be skipped for keyboard or high-frequency actions?
4. Does it respect reduced motion?
5. Is it transform/opacity-based or otherwise performant?

If there is no clear purpose, remove or skip the animation.

## Review Format

For critique, audit, polish, or motion review, prefer:

```markdown
| Before | After | Why |
| --- | --- | --- |
| <current issue> | <specific change> | <user/design reason> |
```

## Guardrails

- Do not turn product UI into a marketing page unless requested.
- Do not add delight before clarity and resilience.
- Do not polish unfinished behavior unless the user explicitly asks for visual exploration.
- Do not hide critical functionality on mobile; adapt it.
- Do not invent new primitives when an existing component should be reused.

## Output

- `Mode`
- `Surface`
- `Main issue`
- `Changes or findings`
- `Verification`
- `Remaining risks`
