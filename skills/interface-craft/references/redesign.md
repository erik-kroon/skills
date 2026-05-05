# Redesign Mode

Use redesign mode when an existing interface should be materially improved
without losing behavior, information architecture, terminology, or product
familiarity.

Redesign mode should upgrade the interface. It should not erase the product's
working shape or make the UI louder than the task requires.

## Redesign Contract

Before changing code, identify:

- What must remain recognizable.
- What behavior must not change.
- Existing design-system primitives to preserve.
- Current failure: hierarchy, density, clarity, responsiveness, states,
  accessibility, or expression.
- Target register: quiet, standard, or expressive.
- Upgrade strategy.
- Risk to usability, accessibility, implementation, or product meaning.

## Upgrade Strategy

Prefer this order:

1. Preserve the core task flow.
2. Fix hierarchy, grouping, spacing, and density.
3. Improve labels, content, and state coverage.
4. Reuse local components and tokens where they still fit.
5. Adjust color, type, media, or motion only when they support the target
   register.

Do not change navigation, density, information priority, or terminology without
a concrete reason.

## Loudness Brake

Before making a visual change stronger, ask:

- Does this help the user understand, decide, or act?
- Is this a brand-first surface, or a repeated-use product surface?
- Would a simpler hierarchy, spacing, copy, or state fix solve the issue?
- Will this still feel appropriate after the tenth use?

If the answer is unclear, choose the quieter option.

## Verification

At minimum verify:

- Core task still works.
- Existing product meaning and terminology are preserved or intentionally
  improved.
- Local design-system conventions are reused where they still fit.
- Target register is visible without creating brand-page theater.
- States, focus, contrast, and responsive behavior are not degraded.

## Output

- `Redesign mode`
- `Current failure`
- `Preserved behavior`
- `Design-system reuse`
- `Upgrade strategy`
- `Verification`
- `Remaining risks`
