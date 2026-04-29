---
name: interface-craft
description: "Improve interface quality through a first-party design operating system: frame, judge, scan, finish, simplify, word, fortify, adapt, compose, type, onboard, speed, systemize, express, and motion. Use for UI/UX/frontend work where taste, usability, resilience, brand fit, performance, or design-system quality matters."
---

# Interface Craft

Use this skill for interface work where the goal is not merely "make it work"
but make it clear, durable, and intentionally designed.

## Preflight

Before changing UI code, state the working context in one line:

```text
INTERFACE_CRAFT: surface=<product|brand|unknown> mode=<mode> context=<loaded|inferred|missing> verification=<planned>
```

Use `product` for tools, dashboards, forms, settings, app shells, and repeated
operational workflows. Use `brand` for marketing pages, portfolios, campaigns,
editorial surfaces, and first-impression pages. If the repo has durable design
guidance, read it before editing. If not, infer cautiously from the existing
surface and name the assumption.

## Choose A Mode

Pick one primary mode from the request. If the request is broad, start with
`frame`, `judge`, or `scan` before changing code.

| Mode | Use when | Reference |
| --- | --- | --- |
| `frame` | Plan UI direction before building or redesigning | [frame.md](references/frame.md) |
| `judge` | Critique experience quality, hierarchy, cognitive load, and fit | [judge.md](references/judge.md) |
| `scan` | Produce prioritized technical interface findings | [scan.md](references/scan.md) |
| `finish` | Complete a nearly shippable interface | [finish.md](references/finish.md) |
| `simplify` | Remove complexity and reduce the interface to what matters | [simplify.md](references/simplify.md) |
| `word` | Improve labels, empty states, errors, instructions, and UX copy | [word.md](references/word.md) |
| `fortify` | Make the interface resilient to edge cases, long text, loading, errors, i18n, and offline states | [fortify.md](references/fortify.md) |
| `adapt` | Make the design work across screen sizes, input methods, or contexts | [adapt.md](references/adapt.md) |
| `compose` | Fix layout, spacing, rhythm, density, and hierarchy | [compose.md](references/compose.md) |
| `type` | Improve typography, readability, font choices, and text hierarchy | [type.md](references/type.md) |
| `onboard` | Improve first-run flows, empty states, activation, and feature discovery | [onboard.md](references/onboard.md) |
| `speed` | Improve perceived and measured interface performance | [speed.md](references/speed.md) |
| `systemize` | Pull repeated patterns into reusable components, tokens, or design-system guidance | [systemize.md](references/systemize.md) |
| `express` | Adjust brand/product expression: bolder, quieter, more colorful, delightful, or technically ambitious | [express.md](references/express.md) |
| `motion` | Decide whether and how motion should exist | [motion.md](references/motion.md) |

Common aliases map naturally: critique -> `judge`, audit -> `scan`, polish ->
`finish`, clarify -> `word`, harden -> `fortify`, distill -> `simplify`,
extract -> `systemize`, bolder/quieter/colorize/delight/overdrive -> `express`,
animate -> `motion`, layout -> `compose`, typeset -> `type`, optimize ->
`speed`.

## Shared Craft Baseline

Always apply these principles:

1. Identify the user's job before changing visuals.
2. Preserve existing design-system conventions unless they are the problem.
3. Make a register call: product surfaces should be efficient and legible;
   brand surfaces can carry more identity and atmosphere.
4. Avoid generic AI tells: identical card grids, purple-blue glow palettes,
   gradient text, decorative glass effects, oversized metric blocks, and default
   type choices.
5. Make hierarchy obvious: primary action, scan path, grouping, and density.
6. Make states complete: default, hover, focus, active, disabled, loading,
   empty, error, success.
7. Verify across at least one narrow and one wide layout when possible.
8. Respect accessibility: labels, contrast, focus, keyboard path, reduced
   motion, touch targets.
9. Prefer fewer high-impact changes over decorative churn.
10. Choose a color, type, spacing, and motion strategy before changing values.

## Motion Decision Gate

Before adding motion:

1. How often will users see it?
2. What purpose does it serve?
3. Can it be skipped for keyboard or high-frequency actions?
4. Does it respect reduced motion?
5. Is it transform/opacity-based or otherwise performant?

If there is no clear purpose, remove or skip the animation.

## Review Format

For judge, scan, finish, simplify, express, or motion review, prefer:

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
- Do not use a visual trope because the domain usually uses it; design from the
  specific audience, setting, and task.
- Keep guidance original and operational; borrow only abstract workflow shape,
  never pasted wording.

## Output

- `Mode`
- `Surface`
- `Context assumption`
- `Main issue`
- `Changes or findings`
- `Verification`
- `Remaining risks`
