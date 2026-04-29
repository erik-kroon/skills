---
name: residue-hunt
description: Find and prioritize cleanup of dead code, fallback masks, mocks, TODO residue, stale bridges, duplicate surfaces, and AI-generated leftovers. Use when the user asks for cleanup candidates, deletion opportunities, residue scans, or stale code review.
---

# Residue Hunt

Use this skill to find cleanup work with evidence before deletion.

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
3. Classify candidates:
   - `confirmed-dead`: no live path found.
   - `likely-dead`: no usage found, but dynamic paths need caution.
   - `fallback-mask`: fallback hides broken or missing real behavior.
   - `mock-residue`: mocks or fixtures escaped their intended scope.
   - `legacy-bridge`: compatibility path that may still have users.
   - `hygiene-residue`: comments, TODOs, debug code, duplicate docs, stale names.
   - `needs-verify`: candidate requires runtime or owner confirmation.
4. Prioritize:
   - Prefer removals that reduce future confusion or prevent wrong extension.
   - Keep rollback-safe sequencing.
5. Recommend action:
   - Delete, consolidate, document, test first, or defer.

## Finding Format

```markdown
| Candidate | Class | Evidence | Recommended action | Confidence |
| --- | --- | --- | --- | --- |
| <path/symbol> | <class> | <usage proof> | <delete/consolidate/verify/defer> | High/Medium/Low |
```

## Guardrails

- Findings must be path-specific and reproducible.
- Do not delete component-library or public API surface from static evidence alone.
- Do not remove legacy bridges without identifying the compatibility risk.
- Do not mix cleanup recommendations with unrelated feature ideas.

## Output

- `Scope`
- `Candidates`
- `Evidence`
- `Recommended sequence`
- `Verification needed`
- `Risks`
