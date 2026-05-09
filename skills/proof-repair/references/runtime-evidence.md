# Runtime Evidence

Use this reference when a bug cannot be proven from existing tests, traces, or
logs. The goal is to gather runtime facts before patching, not to add permanent
observability.

## Contents

- [Trigger](#trigger)
- [Protocol](#protocol)
- [Log Shape](#log-shape)
- [Instrumentation Examples](#instrumentation-examples)
- [Hypothesis Table](#hypothesis-table)
- [Guardrails](#guardrails)

## Trigger

Use runtime evidence when:

- The bug depends on a manual UI flow, browser event, timing, cache, hydration,
  worker, queue, or network sequence.
- Existing failures show only the symptom.
- Multiple subsystems could plausibly be responsible.
- A previous patch was speculative or failed.

## Protocol

1. Write 3-5 falsifiable hypotheses:
   - Each hypothesis names one possible cause.
   - Each hypothesis has a predicted observation that would confirm or reject it.
2. Add temporary structured instrumentation:
   - Put probes at boundaries: user input, event handler entry, state mutation,
     async request start/end, cache read/write, server boundary, serializer,
     queue enqueue/dequeue, and final output.
   - Keep probes small and focused.
   - Map every probe to at least one hypothesis.
3. Mark instrumentation for cleanup:
   - Wrap each probe in language-appropriate markers such as
     `#region proof log` and `#endregion`.
   - Use a unique phrase so `rg "proof log"` finds every temporary block.
4. Capture one clean run:
   - Clear or separate previous logs before the run.
   - Use a `runId` such as `before-fix-1`.
   - Ask the user to reproduce only when automation is not available.
5. Analyze before patching:
   - Mark each hypothesis `Confirmed`, `Rejected`, or `Inconclusive`.
   - Cite the exact log events, line numbers, timestamps, IDs, or request keys.
   - If all hypotheses are rejected, remove speculative code changes, keep only
     useful instrumentation, and generate better hypotheses.
6. Patch the confirmed cause:
   - Keep instrumentation in place for one verification run unless it creates
     unacceptable risk.
   - Use a `runId` such as `after-fix-1`.
7. Clean up:
   - Remove temporary instrumentation after verification or when the user asks.
   - Search for the marker phrase.
   - Review the diff to confirm only the intended fix and durable regression
     guard remain.

## Log Shape

Prefer one JSON object per event. Write to the repo's existing logger, test
output, browser console, or a temporary NDJSON file under `.context/` when a
file is useful.

```json
{
  "runId": "before-fix-1",
  "hypothesisId": "H2",
  "location": "checkout/apply-discount",
  "message": "discount total after cache read",
  "data": {
    "cartId": "cart_123",
    "discountCode": "SPRING",
    "cachedTotal": 4200
  },
  "timestamp": 1778323200000
}
```

Keep payloads compact. Redact tokens, passwords, cookies, personal data, and
large payloads. Prefer IDs, counts, enum values, booleans, and short hashes.

## Instrumentation Examples

JavaScript or TypeScript:

```ts
// #region proof log
console.info(JSON.stringify({
  runId: "before-fix-1",
  hypothesisId: "H1",
  location: "cart/applyCoupon",
  message: "coupon validation result",
  data: { couponId, isValid, reason },
  timestamp: Date.now(),
}));
// #endregion
```

Python:

```py
# region proof log
logger.info({
    "runId": "before-fix-1",
    "hypothesisId": "H1",
    "location": "cart.apply_coupon",
    "message": "coupon validation result",
    "data": {"coupon_id": coupon_id, "is_valid": is_valid},
})
# endregion
```

## Hypothesis Table

```markdown
| ID | Hypothesis | Probe | Predicted evidence | Result |
| --- | --- | --- | --- | --- |
| H1 | <cause> | <log location> | <event/value that proves it> | Confirmed/Rejected/Inconclusive |
```

## Guardrails

- Do not patch before at least one hypothesis has runtime evidence unless an
  existing failing test already proves the cause.
- Do not add broad logging. Every probe must answer a hypothesis.
- Do not keep instrumentation in the final patch unless it is intentionally
  converted into durable observability.
- Do not claim verification from a clean UI alone when logs were required to
  prove the fix.
- Do not leave speculative guards or fallback behavior from rejected hypotheses.
