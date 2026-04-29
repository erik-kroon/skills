---
name: test-first-delivery
description: Build behavior-changing features and bugfixes with a failing-test-first delivery loop. Use when correctness matters, the user asks for TDD, or a change needs a verified behavior contract before implementation.
---

# Test First Delivery

Use this skill when the task is to deliver new or changed behavior, not merely
diagnose an existing failure.

## Workflow

1. Name the behavior contract:
   - What observable behavior should change?
   - Who or what depends on it?
   - What should remain unchanged?
2. Pick the smallest vertical slice:
   - Include the minimum production path needed to prove behavior.
   - Avoid backend-only, frontend-only, or test-only slices unless they produce standalone value.
3. Write the failing test first:
   - Prefer the nearest stable boundary.
   - Assert behavior, not implementation details.
   - Use domain language in test names.
4. Confirm red:
   - Run the focused test.
   - Confirm it fails for the expected reason.
5. Make it green:
   - Implement the smallest change that satisfies the behavior contract.
   - Do not broaden scope while red.
6. Refactor while green:
   - Improve names, boundaries, duplication, and readability.
   - Keep the focused test passing.
7. Broaden verification:
   - Run nearby tests.
   - Run typecheck/build/lint when the touched surface justifies it.
   - Record skipped checks and why.
8. Continue or stop:
   - Add the next behavior slice only if it belongs to the current delivery contract.
   - Otherwise hand off follow-up work explicitly.

## Risk And Verification

Set the verification level before implementation:

- `standard`: focused test plus local sanity check.
- `heightened`: focused test plus nearby suite and type/build check.
- `critical`: explicit regression coverage, broader suite, manual check if user-facing, rollback note.

## Guardrails

- Do not write production code first and backfill tests while calling it TDD.
- Do not test private internals when a stable boundary exists.
- Do not refactor while red unless the test itself is wrong.
- Do not mock fast deterministic code just to isolate implementation.
- Do not keep adding slices after the contract is satisfied.

## Output

- `Behavior contract`
- `Verification level`
- `Red test`
- `Green change`
- `Refactor`
- `Verification`
- `Follow-up slices`
