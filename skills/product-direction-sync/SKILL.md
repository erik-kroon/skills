---
name: product-direction-sync
description: Turn extensive product-direction input into synchronized repo artifacts across docs, README, roadmap notes, and issue/work tracking. Use when a PRD, strategy memo, or direction change needs to update project context instead of becoming one isolated document.
---

# Product Direction Sync

Use this skill to make a substantial product-direction change legible across the repo.

## Workflow

1. Gather source material:
   - User-provided PRD, strategy memo, decision note, transcript, or long-form direction text.
   - Current `README`, `docs/`, roadmap, issue templates, labels, and tracker conventions.
   - Existing product briefs, ADRs, domain context, and open issues when available.
2. Extract the direction delta:
   - What changed.
   - What stays true.
   - New goals, non-goals, constraints, and success signals.
   - Affected users, workflows, surfaces, and repo areas.
   - Decisions made versus questions still open.
3. Map artifacts before editing:
   - Source of truth document to create or update.
   - README sections that need orientation changes.
   - Docs that need additions, links, deprecations, or redirects.
   - Issues or work items to create, update, close, relabel, or leave alone.
   - ADRs needed for durable product or architecture decisions.
4. Present a sync plan unless the change is tiny:
   - Files to update.
   - Tracker actions to propose.
   - Decisions that need human confirmation.
   - Artifacts that should remain unchanged.
5. Apply the smallest coherent artifact update:
   - Keep one canonical direction doc when possible.
   - Update README as an entrypoint, not a duplicate PRD.
   - Link related docs instead of copying large sections.
   - Convert execution work into issue-ready slices only when tracker use is requested or repo convention is clear.
6. Verify consistency:
   - Links resolve.
   - README, docs, and issues do not contradict each other.
   - Deprecated direction is marked or removed.
   - Open questions are easy to find.

## Artifact Targets

- `README.md`: concise orientation, current product direction, and links.
- `docs/`: canonical direction, roadmap, decision, or operating docs.
- `docs/adr/`: durable decisions with tradeoffs and consequences.
- Issue tracker: epics, issues, labels, state changes, or closure notes.
- Agent context: pointers that help future agents find current direction.

## Guardrails

- Do not scatter a long PRD across many files without a canonical source.
- Do not overwrite established repo conventions; extend them carefully.
- Do not create or mutate GitHub issues unless the user asked or repo convention clearly allows it.
- Do not treat open questions as decisions.
- Do not duplicate README and docs content; README should route readers to depth.
- Do not bury direction changes without linking from the repo entrypoint.

## Output

- `Direction delta`
- `Sync plan`
- `Files changed`
- `Issue/work tracking actions`
- `Open decisions`
- `Consistency checks`
