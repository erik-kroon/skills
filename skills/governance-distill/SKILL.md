---
name: governance-distill
description: Maintain prompts, skills, policies, and durable project knowledge by extracting stable rules from repeated work and removing stale or conflicting guidance. Use when agent instructions, skills, docs, or governance are drifting.
---

# Governance Distill

Use this skill to keep agent guidance coherent and durable.

## Workflow

1. Gather source material:
   - Repeated user corrections.
   - Existing skills.
   - Prompt files.
   - ADRs and project docs.
   - Recent workflow failures.
2. Separate signal from incident:
   - Stable rule.
   - One-off preference.
   - Tool limitation.
   - Project-specific convention.
   - Stale instruction.
3. Resolve conflicts:
   - Prefer newer explicit user intent.
   - Prefer repo-specific contracts over generic advice.
   - Remove duplicated or weaker wording.
4. Distill into durable form:
   - Short rule.
   - Trigger condition.
   - Exception.
   - Verification or artifact expectation.
5. Update the right surface:
   - Skill body.
   - Reference doc.
   - README/matrix.
   - Project guidance.
6. Preserve provenance when useful:
   - Note why a rule exists.
   - Link source docs or references.

## Guardrails

- Do not turn every preference into permanent policy.
- Do not add long prose when a short rule works.
- Do not bury critical rules in deep references without a pointer.
- Do not keep conflicting instructions for politeness.

## Output

- `Distilled rules`
- `Changed guidance`
- `Removed or deprecated guidance`
- `Open conflicts`
- `Next maintenance step`
