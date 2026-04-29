# Audit Mode

Use audit mode to produce findings, not fixes.

## Categories

- Accessibility: contrast, ARIA, keyboard path, semantics, alt text, forms.
- Performance: layout thrashing, heavy animations, render churn, image size, bundle weight.
- Theming: hard-coded colors, broken dark mode, inconsistent tokens.
- Responsive: fixed widths, small touch targets, overflow, text scaling, missing breakpoints.
- Anti-patterns: AI tells, nested cards, decorative gradients, redundant copy, generic layouts.

## Finding Format

```markdown
| Severity | Location | Category | Issue | Impact | Recommendation |
| --- | --- | --- | --- | --- | --- |
```

## Severity

- `Critical`: blocks core task or accessibility.
- `High`: significant user harm or likely production issue.
- `Medium`: quality or maintainability issue worth fixing.
- `Low`: polish or minor consistency issue.

## Output

- `Anti-pattern verdict`
- `Executive summary`
- `Detailed findings`
- `Systemic issues`
- `Positive findings`
- `Priority recommendations`
