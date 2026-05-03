# Redesign Mode

Use redesign mode when an existing interface should be materially improved
without losing behavior, information architecture, or product familiarity.

## Redesign Contract

Before changing code, identify:

- What must remain recognizable.
- What behavior must not change.
- Existing design-system primitives to preserve.
- Current visual failure.
- Target register.
- Upgrade strategy.
- Risk to usability, accessibility, or implementation.

## Redesign Moves

- Preserve task flow before changing aesthetics.
- Improve hierarchy before decoration.
- Reuse local components unless they are the source of the problem.
- Reduce generic cards, borders, glows, and placeholder content.
- Keep existing terminology unless it is unclear.
- Upgrade state coverage and responsive behavior.
- Avoid changing navigation, density, or information priority without reason.

## Verification

At minimum verify:

- Core task still works.
- Existing product meaning and terminology are preserved or intentionally
  improved.
- Local design-system conventions are reused where they still fit.
- The target register is visible without creating brand-page theater.
- States, focus, contrast, and responsive behavior are not degraded.

## Output

- `Current failure`
- `Preserved behavior`
- `Design-system reuse`
- `Upgrade strategy`
- `Changes`
- `Verification`
- `Remaining risks`
