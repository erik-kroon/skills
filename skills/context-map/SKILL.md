---
name: context-map
description: Zoom out from unfamiliar code or product area and produce a higher-level map of relevant modules, callers, data flow, domain terms, and where to inspect next. Use when the user asks to zoom out or needs orientation before acting.
---

# Context Map

Use this skill when the user or agent is too deep in details and needs the
surrounding map.

## Workflow

1. Start from the local point:
   - File, symbol, route, feature, issue, or user-described area.
2. Walk outward:
   - Callers.
   - Callees.
   - Entrypoints.
   - Tests.
   - Data models.
   - Docs and ADRs.
3. Name the domain:
   - Use existing glossary terms when present.
   - Flag unclear or overloaded terms.
4. Draw the map:
   - What owns what.
   - What calls what.
   - What data moves where.
   - What is safe to ignore for the current task.
5. Recommend next inspection:
   - Files to read.
   - Tests to run.
   - Skills that fit the next move.

## Guardrails

- Do not solve the problem while mapping unless the answer is trivial.
- Do not include every file found; include what explains the area.
- Do not use generic architecture names when the repo has domain names.
- Keep the map compact enough to act on.

## Output

- `Area`
- `Domain terms`
- `Module map`
- `Call/data flow`
- `Important files`
- `What to ignore`
- `Next inspection`
