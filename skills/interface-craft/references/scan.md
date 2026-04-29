# Scan Mode

Use scan mode to produce prioritized technical interface findings, not broad
taste feedback.

## Categories

- Accessibility: contrast, labels, semantics, keyboard path, focus order, alt
  text, reduced motion, touch targets.
- Performance: slow loading, layout shift, heavy images, render churn, expensive
  animation, unnecessary hydration, oversized bundles.
- Responsiveness: fixed widths, hidden critical actions, overflow, cramped
  touch controls, broken density changes.
- Theming: hard-coded colors, token drift, dark-mode gaps, inconsistent
  elevation, unplanned contrast.
- Interaction states: missing loading, empty, error, success, disabled, pending,
  hover, focus, and active states.
- Anti-patterns: nested cards, repeated card grids, decorative gradients,
  generic hero metrics, unreadable gray text, fragile modals, noisy copy.

## Severity

- `P0`: blocks core task, accessibility, data safety, or purchase/activation.
- `P1`: likely production harm or repeated user failure.
- `P2`: quality, maintainability, or comprehension issue worth scheduling.
- `P3`: polish or consistency issue.

## Finding Format

```markdown
| Severity | Location | Category | Issue | Impact | Recommendation |
| --- | --- | --- | --- | --- | --- |
```

## Output

- `Health verdict`
- `Top risks`
- `Detailed findings`
- `Systemic pattern`
- `Recommended order`
