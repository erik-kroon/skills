---
name: docs-sync
description: Synchronize substantial source material into coherent repo documentation across README, CONTEXT, CONTEXT-MAP, docs, ADRs, roadmap notes, and issue/work tracking. Use when a PRD, strategy memo, decision note, architecture update, or docs drift needs to update canonical repo context instead of becoming one isolated document.
---

# Docs Sync

Use this skill to make substantial direction, architecture, workflow, or context changes legible across the repo's durable documentation.

## Workflow

1. Gather source material:
   - User-provided PRD, strategy memo, decision note, architecture note, transcript, or long-form context.
   - Current `README.md`, `CONTEXT.md`, `CONTEXT-MAP.md`, `docs/`, roadmap, issue templates, labels, and tracker conventions.
   - Existing product briefs, ADRs, domain context, and open issues when available.
2. Extract the documentation delta:
   - What changed.
   - What stays true.
   - New goals, non-goals, constraints, and success signals.
   - Affected users, workflows, modules, surfaces, and repo areas.
   - Decisions made versus questions still open.
3. Map artifacts before editing:
   - Canonical source-of-truth document to create or update.
   - README sections that need orientation or command changes.
   - Context docs that need term, module, workflow, or routing updates.
   - Docs that need additions, consolidation, links, deprecations, or redirects.
   - Issues or work items to create, update, close, relabel, or leave untouched.
   - ADRs needed for durable product or architecture decisions.
4. Present a sync plan unless the change is tiny:
   - Files to update.
   - Tracker actions to propose.
   - Decisions that need human confirmation.
   - Artifacts that should remain unchanged.
5. Apply the smallest coherent artifact update:
   - Keep one canonical doc for each durable topic when possible.
   - Update README as an entrypoint, not a duplicate of deeper docs.
   - Update `CONTEXT.md` for durable domain/product language.
   - Update `CONTEXT-MAP.md` for repo routing and module orientation.
   - Link related docs instead of copying large sections.
   - Convert execution work into issue-ready slices only when tracker use is requested or repo convention is clear.
6. Verify consistency:
   - Links resolve.
   - README, context docs, ADRs, roadmap, and issues do not contradict each other.
   - Deprecated guidance is marked, consolidated, or removed.
   - Open questions are easy to find.

## Artifact Targets

- `README.md`: concise orientation, commands, package map, and links.
- `CONTEXT.md`: durable product/domain context, terms, boundaries, and non-goals.
- `CONTEXT-MAP.md`: short routing map for packages, apps, scripts, tests, and docs.
- `docs/`: canonical roadmap, decision, operating, or research docs.
- `docs/adr/`: durable decisions with tradeoffs and consequences.
- Issue tracker: epics, issues, labels, state changes, or closure notes.
- Agent context: short pointers that help future agents find current repo truth.

## Guardrails

- Do not scatter long-form source material across many files without a canonical source.
- Do not overwrite established repo conventions; extend them carefully.
- Do not create or mutate GitHub issues unless the user asked or repo convention clearly allows it.
- Do not treat open questions as decisions.
- Do not duplicate README and docs content; README should route readers to depth.
- Do not bury durable changes without linking from the repo entrypoint.
- Do not preserve stale docs just because they are detailed; use `docs-debloat` when the right move is deletion, archiving, or consolidation.

## Output

- `Documentation delta`
- `Sync plan`
- `Files changed`
- `Issue/work tracking actions`
- `Open decisions`
- `Consistency checks`
