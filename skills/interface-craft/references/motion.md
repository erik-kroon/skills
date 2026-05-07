# Motion Mode

Use motion mode to decide whether and how an interface should animate.

## Frequency Gate

| Frequency | Decision |
| --- | --- |
| Hundreds of times per day | No animation |
| Tens of times per day | Remove or greatly reduce |
| Occasional | Standard purposeful animation |
| Rare or celebratory | Delight is allowed |

## Purpose Gate

Valid purposes:

- Spatial continuity.
- State indication.
- Feedback.
- Explanation.
- Softening jarring changes.

Invalid purpose:

- "It looks cool" on a frequently used interaction.

## Rules

- Keyboard actions should be instant.
- UI animations should usually stay under 300ms.
- Prefer transform and opacity.
- Avoid `transition: all`.
- Avoid `scale(0)` entry; use `scale(0.95)` plus opacity.
- Popovers should originate from their trigger; modals stay centered.
- Gate hover motion with `(hover: hover) and (pointer: fine)`.
- Use transitions for dynamic interruptible UI; use springs for gestures.
- Respect `prefers-reduced-motion`.
- Use custom easing when motion should feel intentional:
  `cubic-bezier(0.23, 1, 0.32, 1)` for crisp entrances,
  `cubic-bezier(0.77, 0, 0.175, 1)` for movement across the screen, and
  linear only for progress or time.
- Pressable elements should usually have subtle active feedback:
  `transform: scale(0.97)` over 100-160ms.
- Context menus and command palettes used many times per day should skip
  entrance animation entirely.
- Exit can be faster than enter. The system should respond quickly when the
  user releases, cancels, or dismisses.
- Use `@starting-style` for CSS entry transitions when supported.
- Use `clip-path` for reveals, hold-to-confirm affordances, comparison sliders,
  and tab color transitions when it simplifies the DOM.
- For drag, dismissal, and pointer-following interactions, preserve velocity
  with springs and add damping at natural boundaries.
- Capture pointer events during drag and guard multi-touch so the interaction
  does not jump when the pointer leaves the element.
- For touch devices, do not rely on hover-only motion.
- Avoid Framer Motion shorthand `x`, `y`, or `scale` on busy surfaces when a
  CSS `transform` string or CSS transition will stay smoother under load.

## Timing Defaults

| Interaction | Default |
| --- | --- |
| Button press | 100-160ms |
| Tooltip or small popover | 125-200ms |
| Dropdown or select | 150-250ms |
| Modal or drawer | 200-500ms |
| Stagger between items | 30-80ms |
| Hold-to-confirm fill | Deliberate, often 1.5-2s linear |
| Hold release/cancel | Fast, about 200ms ease-out |

## Debugging Motion

- Slow the animation to 2-5x duration and inspect transform origin, opacity,
  color overlap, and property synchronization.
- Check one focal animation at a time; competing motion creates noise.
- Verify reduced-motion behavior keeps helpful opacity or color changes while
  removing movement.
- Test gesture-heavy UI on real touch hardware when possible.

## Review Table

```markdown
| Before | After | Why |
| --- | --- | --- |
```

## Output

- `Motion decision`
- `Before/After/Why table`
- `Reduced motion behavior`
- `Verification`
