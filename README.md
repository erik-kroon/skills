# Erik's Agent Skills

A compact public library of agent skills I use to keep AI-assisted work
rigorous, shippable, and easy to hand off.

This repo is intentionally selective. It is not a backup of every local skill
on my machine. Each public skill has to describe a repeatable work mode, change
agent behavior in a concrete way, and produce an output that is easy to review.

## Skills

| Skill | Use when | Core move |
| --- | --- | --- |
| [signal-cut](skills/signal-cut/SKILL.md) | Scope is too broad or milestone value is fuzzy | Keep, defer, freeze, or remove work around delivery signal |
| [shape-contract](skills/shape-contract/SKILL.md) | Work is ambiguous, risky, or cross-surface | Define posture, requirements, risk tier, decision gates, and verification |
| [context-map](skills/context-map/SKILL.md) | You need to zoom out from unfamiliar code or product area | Map modules, callers, data flow, terms, and next inspection |
| [domain-grill](skills/domain-grill/SKILL.md) | A plan needs pressure-testing against domain language and docs | Resolve terms, assumptions, scenarios, and durable decisions |
| [repo-context-bootstrap](skills/repo-context-bootstrap/SKILL.md) | A repo lacks agent-readable context or skill setup | Establish repo guidance, domain docs, ADR layout, and work conventions |
| [docs-sync](skills/docs-sync/SKILL.md) | Substantial source material needs to update canonical repo docs | Synchronize README, context docs, ADRs, roadmap, and work tracking |
| [docs-debloat](skills/docs-debloat/SKILL.md) | Markdown sprawl needs an aggressive reset | Delete, archive, merge, and rewrite docs into a small canonical set |
| [product-brief](skills/product-brief/SKILL.md) | Conversation or feature intent needs a PRD-style artifact | Turn intent into requirements, constraints, risks, and acceptance checks |
| [work-triage](skills/work-triage/SKILL.md) | Incoming work needs categorization and next state | Move vague intake through a clear state machine |
| [prototype](skills/prototype/SKILL.md) | An idea needs to be tried before production implementation | Build a throwaway logic or UI prototype that answers one question |
| [verticalize-work](skills/verticalize-work/SKILL.md) | A plan needs executable slices or worker-ready tasks | Convert intent into independent vertical slices |
| [test-first-delivery](skills/test-first-delivery/SKILL.md) | Behavior-changing work needs correctness before implementation | Write the failing behavior test, make it pass, refactor while green |
| [proof-repair](skills/proof-repair/SKILL.md) | Behavior is broken, flaky, failing, slow, or incorrect | Build proof, instrument runtime evidence when needed, patch minimally, close verification |
| [performance-research](skills/performance-research/SKILL.md) | Software is slow, resource-heavy, costly, or needs performance review | Frame workload, measure, research the exact stack, patch the bottleneck, and guard against regression |
| [solidjs-best-practices](skills/solidjs-best-practices/SKILL.md) | Solid, Solid Router, or SolidStart code needs writing, review, or refactoring | Shape the reactive graph, async data flow, server boundaries, and bundles around Solid's model |
| [module-deepening](skills/module-deepening/SKILL.md) | Code feels shallow, tangled, hard to test, or hard to navigate | Find deeper modules, simpler interfaces, and better locality |
| [zero-tech-debt](skills/zero-tech-debt/SKILL.md) | A change should be rebuilt as if the intended UX and architecture existed from day one | Delete compatibility cruft, speculative guards, stale fallbacks, wrappers, and accidental complexity |
| [residue-hunt](skills/residue-hunt/SKILL.md) | Code may contain dead paths, fallback masks, speculative guards, wrappers, mode flags, mocks, TODOs, or stale bridges | Surface ranked cleanup suggestions with evidence |
| [contract-review](skills/contract-review/SKILL.md) | A diff or boundary needs risk review | Review correctness, data safety, trust, state, permission, and verification |
| [interface-craft](skills/interface-craft/SKILL.md) | UI/UX/frontend work needs taste, resilience, data density, speed, brand fit, or design-system quality | Choose a mode: create, redesign, frame, judge, scan, finish, simplify, word, fortify, adapt, compose, type, data, onboard, speed, systemize, express, or motion |
| [handoff](skills/handoff/SKILL.md) | Another agent or future session needs to continue current work | Write a compact `.context/` continuation brief with status, risks, and next steps |

## Coverage

The library covers the full loop I want an agent to follow on real work:

- Direction: cut scope, shape contracts, and write product briefs.
- Orientation: map unfamiliar areas, grill domain assumptions, bootstrap repo context, sync docs, and debloat stale markdown.
- Exploration and delivery: prototype uncertain logic or UI, slice work vertically, use test-first delivery, repair failures with proof, and improve performance from measured bottlenecks.
- Quality: deepen modules, apply Solid/SolidStart framework rules, rework patches toward zero tech debt, hunt residue, and review changed contracts.
- Interface craft: create new UI, redesign existing UI, frame direction, judge experience, scan quality, finish details, simplify flow, improve words, fortify edge cases, adapt layouts, compose space, tune type, design dense data surfaces, onboard users, improve speed, systemize patterns, express personality, and tune motion.
- Continuity: triage incoming work into the right next state and preserve handoffs for future sessions or sibling workspaces.

## Docs

- [Skill Matrix](SKILL_MATRIX.md) explains the domain map and when to use each skill.
- [Skill Quality Bar](docs/skill-quality-bar.md) defines the standard for future changes.
- [Skills Inventory](skills-inventory.md) lists the current public collection.

## Layout

```text
skills/
  public skill collection
docs/
  quality criteria
```
