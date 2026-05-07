# Data Mode

Use data mode for dense operational surfaces: tables, dashboards, analytics,
monitoring, finance views, admin queues, comparison tools, and list/detail
workflows where users scan, compare, filter, and act repeatedly.

## Data Contract

Before changing the UI, identify:

- `Primary question`: what the user is trying to answer first.
- `Primary action`: what they do after finding that answer.
- `Density level`: sparse, standard, dense, or expert.
- `Comparison unit`: row, entity, segment, time period, metric, or event.
- `Freshness`: live, recent, stale, cached, delayed, partial, or unknown.
- `Risk`: financial, operational, health, security, compliance, or low-stakes.
- `Failure states`: empty, loading, error, partial data, permission-limited,
  offline, stale, and over-limit.

## Structure

- Start from the task path: overview -> narrow -> compare -> inspect -> act.
- Keep headers, units, filters, and sort state visible where users need them.
- Prefer tables for comparison, lists for scanning, charts for pattern
  recognition, and detail panes for investigation.
- Do not wrap every metric or row in a card. Use alignment, dividers, row
  rhythm, and pinned context first.
- Put filters, search, sort, date range, and saved views in predictable zones.
- Keep bulk actions near selection state, not hidden in generic menus.
- Use progressive disclosure for advanced filters and secondary columns.
- Preserve orientation with breadcrumbs, selected-row state, sticky headers, or
  split panes when moving between list and detail.

## Tables And Lists

- Choose columns by decision value, not data availability.
- Prioritize identity, status, magnitude, change, owner, and next action.
- Align numbers by decimal or unit; use tabular numbers.
- Show units in headers when consistent and in cells when mixed.
- Use explicit timestamps for audit work and relative time only when recency is
  the point.
- Keep row height stable. Secondary details can expand below the row or move to
  a detail pane.
- Make sort direction, active filters, hidden columns, and row selection
  visible.
- Design empty states by cause: no data yet, filtered out, permission denied,
  loading failed, or feature not configured.

## Charts And Metrics

- Every chart must answer a named question.
- Label axes, units, date ranges, sample size, and aggregation.
- Avoid decorative sparklines and unlabeled trend marks.
- Use color for grouping or status, but never as the only signal.
- Show thresholds and baselines when they change interpretation.
- Keep legends close to the chart or label series directly.
- Prefer small multiples when users compare the same metric across segments.

## Interaction

- Keyboard and repeated actions should be instant.
- Search should handle messy input and preserve the user's query.
- Filter changes should be reversible and visible.
- Pagination, infinite scroll, and virtualization must not break selection,
  keyboard navigation, or URL/share state.
- Prefetch only on clear intent: approaching focus, likely next row, opened
  preview, or committed navigation.
- Inline edits need pending, success, error, undo, and conflict behavior.

## Visual System

- Use restrained color and strong hierarchy. Dense UI becomes unreadable when
  every element competes.
- Tint neutrals toward the product palette instead of relying on pure gray.
- Reserve accent color for active state, primary action, or meaningful alerts.
- Use status tokens with icons, labels, or shapes so color is not the only cue.
- Keep typography compact but readable; avoid tiny text that only works on
  desktop.
- Use `font-variant-numeric: tabular-nums` for metrics, tables, prices, counts,
  durations, and aligned identifiers.

## Responsive

- Do not hide the primary action on narrow screens.
- Collapse by priority, not by implementation convenience.
- Use summary rows, pinned identity columns, detail drawers, or drill-in pages
  when the full table cannot fit.
- Touch layouts need larger hit targets, fewer hover-only affordances, and
  clearer selection state.

## Performance

- Use stable dimensions for rows, charts, skeletons, and panels.
- Virtualize only when needed and keep accessibility and find-in-page tradeoffs
  explicit.
- Avoid expensive animation, layout thrash, and unnecessary hydration in dense
  views.
- Compute derived values once, memoize expensive transforms where appropriate,
  and avoid re-rendering the full table for local cell state.

## Output

- `Primary question`
- `Density decision`
- `Structure changes`
- `Data and state coverage`
- `Interaction changes`
- `Responsive behavior`
- `Performance notes`
