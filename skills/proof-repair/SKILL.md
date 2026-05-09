---
name: proof-repair
description: Repair broken, failing, flaky, slow, or incorrect behavior through evidence, root cause, minimal patch, and verification closure. Use for bugs, CI failures, regressions, incidents, and stabilization work.
---

# Proof Repair

Use this skill when correctness is already broken or suspected broken.

Core rule: no fixes without root cause evidence first. A tempting patch is not a
repair until the failure has a proof loop, a traced cause, and a verification
path.

## Runtime Evidence Mode

When the failure cannot be explained from an existing test, stack trace, or log,
switch to runtime evidence mode. Read
[runtime-evidence.md](references/runtime-evidence.md) and use lightweight,
temporary instrumentation to prove or reject hypotheses before patching.

Use runtime evidence mode for:

- UI bugs that require a user flow to reproduce.
- State, timing, hydration, cache, race, or event-ordering bugs.
- Flaky behavior where normal tests only show the symptom.
- Multi-boundary failures where values change across client/server, queue,
  worker, database, browser, or framework boundaries.

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
   - For runtime-only bugs, add temporary structured logs that map each probe to
     a hypothesis, then reproduce and analyze the logs.
   - Change one variable at a time.
6. Patch minimally:
   - Fix the confirmed cause.
   - Avoid broad redesign while stabilizing.
   - If three fixes have failed, stop and question the architecture before
     stacking another patch.
7. Close verification:
   - Original proof loop passes.
   - Nearest broader checks pass or blockers are stated.
   - Temporary probes and instrumentation are removed after verification.
   - Useful regression coverage remains.

## Debugging Patterns

- Backward trace: when an error appears deep in the stack, ask "what called
  this with this value?" until the source is found. Fix at the source, then add
  guardrails near dangerous operations.
- Boundary instrumentation: in multi-component systems, log what enters and
  exits each boundary before proposing a fix.
- Hypothesis matrix: create 3-5 plausible causes, define the exact observation
  that would prove or reject each one, then instrument all of them in one run
  when possible.
- Structured runtime logs: write one JSON object per event with a run id,
  hypothesis id, location, message, and compact data payload so evidence can be
  compared across reproduction attempts.
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
- Do not leave temporary instrumentation in the final patch unless the user
  explicitly wants durable observability.
- Do not keep code changes made for rejected hypotheses.

## Output

- `Failure`
- `Proof loop`
- `Investigation`
- `Root cause`
- `Patch`
- `Verification`
- `Residual risk`
