---
name: verticalize-work
description: Convert a plan, PRD, idea, or backlog into independently executable vertical slices without assuming a specific issue tracker. Use when the user wants tickets, worker prompts, implementation slices, or a plan broken into agent-ready work.
---

# Verticalize Work

Use this skill to turn intent into executable work.

## Workflow

1. Define the outcome:
   - What should be true when all slices are done?
2. Identify horizontal temptations:
   - Separate backend-only, frontend-only, test-only, or cleanup-only tasks.
   - Merge them when they do not produce standalone value.
3. Create the tracer slice:
   - Thin end-to-end path.
   - Observable behavior.
   - Minimal surface.
4. Add depth slices:
   - Coverage, edge cases, integrations, hardening, polish, cleanup.
5. Make each slice grabbable:
   - Goal.
   - Scope.
   - Files or areas to inspect.
   - Acceptance criteria.
   - Verification.
   - Dependencies.
6. Choose output format:
   - Markdown issue.
   - Worker prompt.
   - Checklist.
   - Issue tracker payload only if the user asks.

## Slice Template

```markdown
## Goal

## Scope

## Acceptance Criteria

- [ ] <observable result>

## Verification

## Dependencies
```

## Guardrails

- Do not create "setup", "backend", "frontend", and "tests" slices unless each has standalone value.
- Do not hide discovery; make it an explicit first slice when needed.
- Do not assume a specific tracker or local markdown workflow unless the user specifies.
- Do not make every slice the same size; make every slice independently useful.

## Output

- `Outcome`
- `Slice strategy`
- `Ordered slices`
- `Dependencies`
- `Suggested first slice`
