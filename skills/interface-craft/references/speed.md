# Speed Mode

Use speed mode to improve perceived and measured interface performance.

## Assess

- What feels slow to the user?
- Is the issue loading, interaction latency, animation jank, layout shift, or
  unnecessary work?
- Which route, component, asset, or data dependency is on the critical path?
- Are images, fonts, scripts, and data requests sized and sequenced well?
- Does the UI show useful progress without fake busyness?

## Moves

- Protect layout stability with known dimensions and skeletons where useful.
- Reduce render churn, unnecessary state, and expensive derived work.
- Defer non-critical code and media.
- Optimize images, fonts, and above-the-fold assets.
- Keep animations on compositor-friendly properties.
- Prefer perceived speed improvements when raw speed cannot change quickly.
- Measure before and after when tooling exists.

## Output

- `Performance issue`
- `Evidence`
- `Changes`
- `Measured or perceived impact`
- `Remaining bottlenecks`
