---
name: domain-grill
description: Stress-test a plan, feature, or architecture decision against repo domain language, existing code, and documented decisions. Use when the user wants to be grilled, terminology is fuzzy, or a decision should update CONTEXT.md or ADRs.
---

# Domain Grill

Use this skill to turn fuzzy intent into precise domain language and durable
decisions.

## Workflow

1. Load the map:
   - Read `CONTEXT.md`, `CONTEXT-MAP.md`, ADRs, and nearby code when present.
   - If none exist, infer current language from code and docs.
2. Identify the decision tree:
   - Terms that are overloaded.
   - Assumptions that are unproven.
   - Domain relationships that need examples.
   - Decisions that may deserve an ADR.
3. Ask focused questions:
   - One decision at a time.
   - If code can answer the question, inspect code instead of asking.
   - Provide a recommended answer when useful.
4. Resolve language:
   - Prefer project vocabulary.
   - Add or update domain terms when the user confirms them.
5. Record durable outcomes:
   - Update `CONTEXT.md` for domain language.
   - Offer an ADR only when the decision is hard to reverse, surprising, and tradeoff-driven.

## Guardrails

- Do not interview for facts the repo can answer.
- Do not batch many questions when one decision blocks the next.
- Do not create ADRs for obvious or temporary choices.
- Do not let vague terms survive when a canonical term is available.

## Output

- `Decision under grill`
- `Resolved terms`
- `Confirmed assumptions`
- `Open questions`
- `Docs to update`
- `Recommended next decision`
