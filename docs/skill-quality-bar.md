# Skill Quality Bar

This repo should stay small. A skill earns its place when it changes agent
behavior in a way a normal prompt would not reliably do.

## Required Shape

Each public skill must have:

- `name` and `description` frontmatter.
- A precise trigger in the description.
- One primary job.
- A concrete workflow.
- Guardrails.
- A predictable output contract.
- No dependency on a specific service unless the skill is explicitly about that service.

## Good Skill Signals

- It makes the agent stop and build evidence before acting.
- It names the unit of work.
- It gives a loop, not a lecture.
- It has checkpoints where wrong assumptions are caught.
- It tells the agent what not to do.
- It makes the final output easy to inspect.
- It uses repo-local language and patterns instead of generic architecture advice.

## Bad Skill Signals

- It is a long essay with no operational loop.
- It mixes unrelated jobs.
- It requires private context to understand the name.
- It is mostly a list of preferences.
- It duplicates another skill with slightly different wording.
- It is tied to a product, CLI, or service without being intentionally scoped that way.

## Revision Rule

When a new skill idea appears, first try to map it to the matrix:

1. If an existing skill covers it, improve that skill.
2. If two skills cover it awkwardly, clarify their boundary.
3. If no skill covers it and the workflow is repeatable, add a new skill.

## Naming Rule

Use names that say what the skill does:

- Good: `diagnose-first`, `scope-cut`, `test-first-slice`.
- Weak: internal codenames, role names, or jokes that require private context.
