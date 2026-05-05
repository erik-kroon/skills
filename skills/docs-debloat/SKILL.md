---
name: docs-debloat
description: Aggressively reset bloated repository documentation into a small set of durable canonical docs. Use when a repo has too many markdown files, stale plans, generated reports, agent notes, old PRDs, duplicated context, or documentation that should be deleted, archived, or consolidated.
---

# Docs Debloat

Use this skill for a heavy documentation reset. Treat markdown as disposable operational scaffolding unless it contains durable product, architecture, or workflow truth. Optimize for making the repo legible, not for preserving every document.

Use `repo-context-bootstrap` in strict minimal durable context mode when the repo lacks clear entrypoints, domain context, or ADR conventions.

## Target Shape

Prefer a small canonical set:

- `README.md`: public/project-facing overview, install, commands, package map, and short product explanation.
- `CONTEXT.md`: durable domain/product context, terms, boundaries, non-goals, and current architecture summary.
- `CONTEXT-MAP.md`: short monorepo routing map for packages, apps, registry, scripts, tests, and docs.
- `docs/adr/`: only durable architecture decisions that still match current code.
- `docs/roadmap.md` or `docs/roadmap/`: optional, current, actionable roadmap only.
- `docs/reports/`: usually delete or archive; reports are snapshots.
- `docs/research/`: usually archive or delete unless curated research informs current architecture.
- `AGENTS.md` or equivalent: at most one short repo-local agent entrypoint that points to canonical docs.

## Workflow

1. Inventory markdown:
   - Find markdown outside dependency/vendor/reference dumps.
   - Build a table with `file`, `purpose`, `status`, `decision`, and `reason`.
   - Classify each file as `keep`, `rewrite`, `merge`, `delete`, or `archive`.
2. Identify source-of-truth docs:
   - Decide which files should remain canonical.
   - Prefer one canonical doc over several overlapping docs.
   - Avoid creating new docs unless they replace many old ones.
3. Detect duplication:
   - Product boundaries.
   - Architecture/package layout.
   - Provider, registry, or workflow policies.
   - Roadmap, PRD, issue inventory, and agent instructions.
4. Detect staleness:
   - Search for old package names, removed paths, stale providers, old architecture names, local absolute paths, dirty worktree notes, issue counts, stale env vars, TODO/FIXME residue, and agent/tooling noise.
   - Classify hits; do not blindly delete every match.
5. Delete, merge, or archive:
   - Prefer deletion when a file has no durable value.
   - Archive only when historical value is real and future agents should not read it by default.
   - If archiving, use `docs/archive/YYYY-MM-DD-<name>.md`.
   - Do not let archive become a new junk drawer.
6. Rewrite canonical docs to be short:
   - `README.md`: enough for humans, not exhaustive.
   - `CONTEXT.md`: ideally under 150-250 lines.
   - `CONTEXT-MAP.md`: ideally under 100-150 lines.
   - `AGENTS.md`: ideally under 80 lines.
   - ADRs: one durable decision each.
7. Move task inventories out of docs:
   - If a markdown file is a backlog, PRD queue, issue inventory, future-work catalog, or implementation diary, convert it to tracker work only when requested or clearly conventional.
   - Otherwise delete it if it is already represented elsewhere or no longer actionable.
8. Verify:
   - Check links in remaining docs.
   - Re-run stale-term searches.
   - Search for local absolute paths and agent/tooling noise.
   - Run repo verification commands when available and relevant.

## Anti-Goals

- No multiple overlapping PRDs.
- No stale generated reports.
- No agent vertical notes as primary docs.
- No long issue inventories in the repo when an issue tracker owns active work.
- No giant end-state component catalogs unless converted into active work.
- No local absolute paths or dirty worktree notes.
- No docs that describe removed architecture.
- No docs that repeat README in different words.
- No docs that are only useful to one AI agent session.
- No source code changes unless needed to fix documentation links.
- No new documentation framework.

## Output

- `Current context`
- `Documentation inventory`
- `Debloat plan`
- `Files changed`
- `Canonical docs after reset`
- `Deleted/archived docs`
- `Remaining questions`
- `Future agent entrypoint`
