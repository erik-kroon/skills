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
