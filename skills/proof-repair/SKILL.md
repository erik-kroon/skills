---
name: proof-repair
description: Repair broken, failing, flaky, slow, or incorrect behavior through evidence, root cause, minimal patch, and verification closure. Use for bugs, CI failures, regressions, incidents, and stabilization work.
---

# Proof Repair

Use this skill when correctness is already broken or suspected broken.

Core rule: no fixes without root cause evidence first. A tempting patch is not a
repair until the failure has a proof loop, a traced cause, and a verification
path.

## Workflow

1. Capture the failure:
   - Exact symptom, command, error, trace, screenshot, or timing.
2. Build a proof loop:
   - Failing test, CLI command, HTTP request, browser script, fixture replay, or minimal harness.
   - For flaky failures, measure the failure rate.
3. Confirm scope:
   - The loop must fail for the user-described reason, not a nearby reason.
4. Investigate before fixing:
   - Read the complete error, stack trace, warning, and relevant logs.
   - Reproduce consistently or state why reproduction is not yet possible.
   - Check recent changes, dependency/config changes, and environment
     differences.
   - Find similar working examples and compare differences.
5. Trace root cause:
   - Form falsifiable hypotheses.
   - Trace bad values backward through callers until the original trigger is
     found.
   - Add the smallest useful probe at component boundaries: input, output,
     environment/config propagation, and state.
   - Change one variable at a time.
6. Patch minimally:
   - Fix the confirmed cause.
   - Avoid broad redesign while stabilizing.
   - If three fixes have failed, stop and question the architecture before
     stacking another patch.
7. Close verification:
   - Original proof loop passes.
   - Nearest broader checks pass or blockers are stated.
   - Temporary probes are removed.
   - Useful regression coverage remains.

## Debugging Patterns

- Backward trace: when an error appears deep in the stack, ask "what called
  this with this value?" until the source is found. Fix at the source, then add
  guardrails near dangerous operations.
- Boundary instrumentation: in multi-component systems, log what enters and
  exits each boundary before proposing a fix.
- Condition-based waiting: replace arbitrary sleeps with waits for the actual
  event, state, file, count, or URL. Keep arbitrary waits only when testing
  known timing behavior and document why.
- Defense in depth: when invalid data caused the failure, validate at entry,
  business logic, environment-specific danger points, and useful forensic logs.
- Pattern comparison: read the closest working implementation completely before
  adapting it.

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
- Do not fix where the symptom appears if the source can be traced.
- Do not bundle multiple hypotheses into one change.
- Do not use sleeps for async behavior unless the delay itself is the behavior
  under test.

## Output

- `Failure`
- `Proof loop`
- `Investigation`
- `Root cause`
- `Patch`
- `Verification`
- `Residual risk`
