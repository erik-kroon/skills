---
name: proof-repair
description: Repair broken, failing, flaky, slow, or incorrect behavior through evidence, root cause, minimal patch, and verification closure. Use for bugs, CI failures, regressions, incidents, and stabilization work.
---

# Proof Repair

Use this skill when correctness is already broken or suspected broken.

## Workflow

1. Capture the failure:
   - Exact symptom, command, error, trace, screenshot, or timing.
2. Build a proof loop:
   - Failing test, CLI command, HTTP request, browser script, fixture replay, or minimal harness.
   - For flaky failures, measure the failure rate.
3. Confirm scope:
   - The loop must fail for the user-described reason, not a nearby reason.
4. Find root cause:
   - Form falsifiable hypotheses.
   - Add the smallest useful probe.
   - Change one variable at a time.
5. Patch minimally:
   - Fix the confirmed cause.
   - Avoid broad redesign while stabilizing.
6. Close verification:
   - Original proof loop passes.
   - Nearest broader checks pass or blockers are stated.
   - Temporary probes are removed.
   - Useful regression coverage remains.

## Hypothesis Record

```markdown
| Hypothesis | Prediction | Probe | Result |
| --- | --- | --- | --- |
| <cause> | <what should happen if true> | <test/log/change> | Confirmed/Rejected |
```

## Guardrails

- No speculative patch stacks.
- No root cause claim without evidence.
- No broad refactor inside repair scope unless necessary for the fix.
- If no proof loop is possible, state what was tried and what artifact is missing.

## Output

- `Failure`
- `Proof loop`
- `Root cause`
- `Patch`
- `Verification`
- `Residual risk`
