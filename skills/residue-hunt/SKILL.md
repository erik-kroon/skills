---
name: residue-hunt
description: Surface evidence-backed cleanup suggestions for dead code, fallback masks, speculative guards, wrappers, mode flags, mocks, TODO residue, stale bridges, duplicate surfaces, and AI-generated leftovers. Use when the user asks for cleanup candidates, deletion opportunities, residue scans, or stale code review.
---

# Residue Hunt

Use this skill to surface cleanup suggestions with evidence. Default to a
ranked suggestion list, similar to `improve-codebase-architecture`: identify
opportunities, explain the friction they cause, recommend the shape of the
cleanup, and ask which one the user wants to pursue before making changes.

This is the cleanup-finder companion to `zero-tech-debt`: hunt for cruft an
agent may have added "just in case", then classify it with evidence before any
deletion or refactor.

## Workflow

1. Define the hunting ground:
   - Changed files, module, package, route, feature, or entire repo.
2. Scan evidence:
   - Entrypoints.
   - Imports and call sites.
   - Tests.
   - Runtime references.
   - Git history when useful.
   - Docs and TODOs.
   - Wrappers, adapters, flags, alternate modes, and compatibility branches.
   - Fallbacks or guards whose only evidence is defensive imagination.
3. Classify suggestions:
   - `confirmed-dead`: no live path found.
   - `likely-dead`: no usage found, but dynamic paths need caution.
   - `fallback-mask`: fallback hides broken or missing real behavior.
   - `speculative-cruft`: guard, wrapper, mode flag, fallback, branch, or
     abstraction exists for hypothetical callers or future options.
   - `mock-residue`: mocks or fixtures escaped their intended scope.
   - `legacy-bridge`: compatibility path that may still have users.
   - `hygiene-residue`: comments, TODOs, debug code, duplicate docs, stale names.
   - `needs-verify`: candidate requires runtime or owner confirmation.
4. Prioritize:
   - Prefer removals that reduce future confusion or prevent wrong extension.
   - Keep rollback-safe sequencing.
5. Present suggestions:
   - Files and symbols involved.
   - Problem caused by the residue.
   - Evidence that the residue is stale, risky, or confusing.
   - Suggested cleanup shape: delete, consolidate, document, test first, or defer.
   - Confidence and verification needed.
6. Ask the user which suggestion to pursue.

Do not edit files during the default scan unless the user explicitly asked for
cleanup implementation. When implementation is requested, make the smallest
safe change and preserve the same evidence trail in the final answer.

## Suggestion Format

```markdown
1. **<short suggestion title>**
   - Files: `<paths/symbols>`
   - Class: `<class>`
   - Problem: `<why this residue causes friction or risk>`
   - Evidence: `<usage proof, missing call sites, stale docs, or runtime caveat>`
   - Suggested cleanup: `<delete/consolidate/document/test first/defer>`
   - Confidence: `<High/Medium/Low>`
   - Verification needed: `<exact check or owner confirmation>`
```

## Guardrails

- Findings must be path-specific and reproducible.
- Do not delete component-library or public API surface from static evidence alone.
- Do not remove legacy bridges without identifying the compatibility risk.
- Do not mix cleanup recommendations with unrelated feature ideas.
- Prefer a concise suggestion list over exhaustive low-value findings.
- Stop at suggestions by default; only implement when asked.

## Output

- `Scope`
- `Suggestions`
- `Recommended sequence`
- `Verification needed`
- `Risks`
- `Question: Which suggestion should I pursue?`
