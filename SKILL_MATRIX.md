# Skill Matrix

This matrix keeps the collection easy to inspect. Each skill earns its place by
covering a distinct work mode with a concrete trigger, workflow, guardrails, and
output contract.

## Domain Coverage

| Domain | Skills | What they protect |
| --- | --- | --- |
| Direction and scope | `signal-cut`, `shape-contract`, `product-brief` | Prevents vague goals, oversized milestones, and premature implementation |
| Context and decisions | `context-map`, `domain-grill`, `repo-context-bootstrap`, `docs-sync`, `docs-debloat` | Keeps agents grounded in repo language, architecture, documented decisions, and canonical docs |
| Delivery and repair | `verticalize-work`, `test-first-delivery`, `proof-repair`, `performance-research` | Turns intent into shippable slices and keeps behavior evidence-backed |
| Framework practice | `solidjs-best-practices` | Prevents React instincts from breaking Solid reactivity, async data, SSR, and bundle boundaries |
| Code quality | `module-deepening`, `residue-hunt`, `contract-review` | Improves boundaries, suggests stale-complexity cleanup, and reviews real risk |
| Interface quality | `interface-craft` | Applies taste, usability, data-density, resilience, and design-system discipline without making UI louder than the task requires |
| Continuity | `work-triage` | Keeps incoming work classifiable |

## Public Skills

| Skill | Job | Why it belongs |
| --- | --- | --- |
| `signal-cut` | Reduce scope to delivery signal | Prevents milestone drift before implementation starts |
| `shape-contract` | Shape ambiguous work into requirements, risk, gates, and verification | Converts ambiguity into a buildable contract |
| `context-map` | Zoom out from unfamiliar code or product area | Gives orientation without jumping to action |
| `domain-grill` | Pressure-test a plan against domain language and docs | Resolves terms, assumptions, and durable decisions |
| `repo-context-bootstrap` | Set up repo-local agent context | Makes future skill use reliable in a repo |
| `docs-sync` | Synchronize substantial source material into canonical repo docs | Prevents PRDs, strategy memos, architecture updates, or decision notes from becoming isolated artifacts |
| `docs-debloat` | Reset bloated markdown into a small durable doc set | Deletes, archives, merges, and rewrites stale docs so future agents know where to start |
| `product-brief` | Produce PRD-style product artifacts | Freezes intent without assuming a tracker |
| `work-triage` | Categorize and state incoming work | Turns vague intake into actionable next artifacts |
| `verticalize-work` | Break plans into executable vertical slices | Creates worker-ready tasks without horizontal backlog sludge |
| `test-first-delivery` | Build behavior with a failing-test-first loop | Keeps correctness work explicit and inspectable |
| `proof-repair` | Repair broken behavior with evidence | Keeps stabilization root-cause-first |
| `performance-research` | Improve performance from measured bottlenecks and current stack research | Prevents generic optimization advice and stale performance folklore |
| `solidjs-best-practices` | Apply Solid.js, Solid Router, and SolidStart best practices | Keeps Solid work aligned to fine-grained reactivity, router data APIs, SSR boundaries, owners, and bundle discipline |
| `module-deepening` | Improve architecture through deeper modules and clearer seams | Makes architecture work concrete and testability-oriented |
| `residue-hunt` | Suggest cleanup and deletion opportunities | Turns cleanup into evidence-backed suggestions rather than taste debate |
| `contract-review` | Review changed contracts and risks | Makes review concrete, scoped, and risk-oriented |
| `interface-craft` | Operate UI quality through explicit modes | Preserves deep UI taste without fragmenting the library |

## When To Use Which

| Situation | Start with |
| --- | --- |
| The idea is too broad or the MVP keeps expanding | `signal-cut` |
| Requirements are ambiguous or risky | `shape-contract` |
| You need a product artifact from conversation context | `product-brief` |
| The codebase area is unfamiliar | `context-map` |
| A plan uses fuzzy domain language | `domain-grill` |
| A repo needs durable agent context | `repo-context-bootstrap` |
| Source material needs to update README, context, ADRs, roadmap, or tracker work | `docs-sync` |
| Markdown docs are stale, duplicated, generated, or too numerous | `docs-debloat` |
| A plan needs worker-ready slices | `verticalize-work` |
| Correct behavior should drive implementation | `test-first-delivery` |
| Something is broken, flaky, failing, or slow | `proof-repair` |
| Software is slow, resource-heavy, costly, or needs performance review | `performance-research` |
| Solid, Solid Router, or SolidStart code needs implementation, review, or refactoring | `solidjs-best-practices` |
| The architecture feels shallow or tangled | `module-deepening` |
| You suspect dead code, mocks, fallbacks, or stale bridges | `residue-hunt` |
| A diff or boundary needs review | `contract-review` |
| UI needs creation, redesign, framing, critique, audit, finishing, copy, hardening, adaptation, layout, typography, dense data design, onboarding, performance, systemization, expression, or motion review | `interface-craft` |
| Incoming work needs a state and next action | `work-triage` |

## Interface-Craft Modes

| Mode | Output |
| --- | --- |
| `create` | New UI with register, primary job, state coverage, and responsive verification |
| `redesign` | Existing UI upgrade that preserves behavior and avoids unnecessary loudness |
| `frame` | Design brief before UI implementation |
| `judge` | Experience quality, cognitive-load, and persona feedback |
| `scan` | Severity-ranked interface findings |
| `finish` | Before/after quality pass |
| `simplify` | Removed complexity and simplified flow |
| `word` | Copy and terminology improvements |
| `fortify` | Edge-case and resilience fixes |
| `adapt` | Context and device adaptation |
| `compose` | Layout, spacing, rhythm, and hierarchy improvements |
| `type` | Typography and readability improvements |
| `data` | Dense tables, dashboards, analytics, monitoring, and operational data surfaces |
| `onboard` | First-run, empty-state, and activation improvements |
| `speed` | Interface performance improvements |
| `systemize` | Reusable components, tokens, and patterns |
| `express` | Controlled expressive adjustment |
| `motion` | Motion decision and review table |

## Add-A-Skill Rule

Add a new public skill only when it introduces a new work mode that cannot be
cleanly expressed as a mode or reference inside an existing skill.
