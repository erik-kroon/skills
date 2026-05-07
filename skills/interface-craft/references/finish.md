# Finish Mode

Use finish mode only when the interface is functionally close to done.

## Passes

- Alignment and spacing: consistent rhythm, optical balance, no accidental gaps.
- Typography: clear hierarchy, readable line length, stable weights, good
  wrapping.
- Color and contrast: intentional emphasis, accessible contrast, coherent
  tokens.
- State completeness: hover, focus, active, disabled, loading, empty, error,
  success, pending.
- Interaction detail: controls respond clearly without slowing repeated work.
- Motion detail: no `transition: all`, no `scale(0)` entries, no slow
  high-frequency animations, and popovers originate from their trigger.
- Content: labels, errors, help text, and empty states are specific.
- Icons and media: aligned, sized, purposeful, and not decorative clutter.
- Forms: labels, validation, helper text, grouping, and submission feedback.
- Responsive behavior: narrow, medium, and wide layouts preserve priority.
- Code quality: remove dead comments, logs, unused imports, duplicate styles.
- Data polish: numbers align, units and timestamps are unambiguous, dense rows
  remain scannable, and status color never carries meaning alone.

## Checklist

- [ ] Primary task is obvious.
- [ ] Focus and keyboard path work.
- [ ] Touch targets are large enough.
- [ ] No text overflow or layout shift.
- [ ] Reduced motion is respected.
- [ ] Loading and error states are useful.
- [ ] Visual choices match the product or brand register.
- [ ] Pressable controls have intentional active feedback.
- [ ] Popovers, menus, and tooltips appear from the right origin.
- [ ] Tables, charts, and metrics answer a real user question.
- [ ] Defaults are good enough that most users should not need configuration.

## Fresh-Eye Pass

When motion, dense data, or complex state is involved, review once at normal
speed and once slowed down. Look for timing mismatches, flicker, overlapping
states, layout shift, unclear focus, and content that only works with perfect
demo data.

## Output

- `Finish changes`
- `Before/After/Why table`
- `Verification`
- `Remaining finish work`
