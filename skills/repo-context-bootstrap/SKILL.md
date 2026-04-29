---
name: repo-context-bootstrap
description: "Set up or repair repo-local agent context: agent guidance, domain docs, ADR layout, issue/work tracking conventions, labels, and skill usage notes. Use before applying a skill collection to a repo or when agents lack repo context."
---

# Repo Context Bootstrap

Use this skill to make a repo legible to future agents.

## Workflow

1. Inspect the repo:
   - Agent guidance files, `CONTEXT.md`, `CONTEXT-MAP.md`, `docs/adr/`, issue docs, queue docs, and remotes.
2. Identify missing context:
   - Where domain terms live.
   - Where decisions live.
   - Where work items live.
   - Which skills should be used in this repo.
   - What labels or states are used for triage.
3. Present a bootstrap plan:
   - Files to create.
   - Files to update.
   - Conventions to record.
   - Questions that genuinely block setup.
4. Write minimal durable docs:
   - Prefer short sections and pointers.
   - Avoid locking in tool-specific workflow unless the repo already uses it.
5. Verify:
   - Links are valid.
   - Instructions do not duplicate or conflict.
   - Future agents can find domain, decisions, work tracking, and skill guidance.

## Suggested Files

- Agent entrypoint file: repo-local operating guidance.
- `CONTEXT.md`: domain glossary and concepts.
- `CONTEXT-MAP.md`: monorepo context routing.
- `docs/adr/`: durable architecture decisions.
- `docs/agents/`: issue tracker, triage labels, skill conventions.

## Guardrails

- Do not create multiple agent entrypoint files unless the repo already uses them.
- Do not overwrite existing guidance; merge carefully.
- Do not invent issue tracker conventions when the repo already has one.
- Keep setup docs short enough to be read.

## Output

- `Current context`
- `Bootstrap plan`
- `Files changed`
- `Remaining setup questions`
- `How future agents should use this repo`
