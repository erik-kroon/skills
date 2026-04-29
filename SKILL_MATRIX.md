# Skill Matrix

This matrix keeps the collection easy to inspect. Each skill earns its place by
covering a distinct work mode with a concrete trigger, workflow, guardrails, and
output contract.

## Domain Coverage

| Domain | Skills | What they protect |
| --- | --- | --- |
| Direction and scope | `signal-cut`, `shape-contract`, `product-brief` | Prevents vague goals, oversized milestones, and premature implementation |
| Context and decisions | `context-map`, `domain-grill`, `repo-context-bootstrap` | Keeps agents grounded in repo language, architecture, and documented decisions |
| Delivery and repair | `verticalize-work`, `test-first-delivery`, `proof-repair` | Turns intent into shippable slices and keeps behavior evidence-backed |
| Code quality | `module-deepening`, `residue-hunt`, `contract-review` | Improves boundaries, removes stale complexity, and reviews real risk |
| Interface quality | `interface-craft` | Applies taste, usability, resilience, and design-system discipline to UI work |
| Continuity and governance | `handoff-brief`, `work-triage`, `governance-distill` | Keeps work resumable, classifiable, and aligned with durable guidance |

## Public Skills

| Skill | Job | Why it belongs |
| --- | --- | --- |
| `signal-cut` | Reduce scope to delivery signal | Prevents milestone drift before implementation starts |
| `shape-contract` | Shape ambiguous work into requirements, risk, gates, and verification | Converts ambiguity into a buildable contract |
| `context-map` | Zoom out from unfamiliar code or product area | Gives orientation without jumping to action |
| `domain-grill` | Pressure-test a plan against domain language and docs | Resolves terms, assumptions, and durable decisions |
| `repo-context-bootstrap` | Set up repo-local agent context | Makes future skill use reliable in a repo |
| `product-brief` | Produce PRD-style product artifacts | Freezes intent without assuming a tracker |
| `work-triage` | Categorize and state incoming work | Turns vague intake into actionable next artifacts |
| `verticalize-work` | Break plans into executable vertical slices | Creates worker-ready tasks without horizontal backlog sludge |
| `test-first-delivery` | Build behavior with a failing-test-first loop | Keeps correctness work explicit and inspectable |
| `proof-repair` | Repair broken behavior with evidence | Keeps stabilization root-cause-first |
| `module-deepening` | Improve architecture through deeper modules and clearer seams | Makes architecture work concrete and testability-oriented |
| `residue-hunt` | Find cleanup and deletion opportunities | Turns cleanup into evidence-backed work rather than taste debate |
| `contract-review` | Review changed contracts and risks | Makes review concrete, scoped, and risk-oriented |
| `interface-craft` | Operate UI quality through explicit modes | Preserves deep UI taste without fragmenting the library |
| `handoff-brief` | Preserve continuity across sessions or agents | Makes continuation safe |
| `governance-distill` | Maintain prompts, skills, policies, and durable knowledge | Keeps the agent system coherent over time |

## When To Use Which

| Situation | Start with |
| --- | --- |
| The idea is too broad or the MVP keeps expanding | `signal-cut` |
| Requirements are ambiguous or risky | `shape-contract` |
| You need a product artifact from conversation context | `product-brief` |
| The codebase area is unfamiliar | `context-map` |
| A plan uses fuzzy domain language | `domain-grill` |
| A repo needs durable agent context | `repo-context-bootstrap` |
| A plan needs worker-ready slices | `verticalize-work` |
| Correct behavior should drive implementation | `test-first-delivery` |
| Something is broken, flaky, failing, or slow | `proof-repair` |
| The architecture feels shallow or tangled | `module-deepening` |
| You suspect dead code, mocks, fallbacks, or stale bridges | `residue-hunt` |
| A diff or boundary needs review | `contract-review` |
| UI needs critique, audit, polish, copy, hardening, adaptation, simplification, expression, extraction, or motion review | `interface-craft` |
| Work needs to survive a handoff | `handoff-brief` |
| Incoming work needs a state and next action | `work-triage` |
| Instructions or durable docs are drifting | `governance-distill` |

## Interface-Craft Modes

| Mode | Output |
| --- | --- |
| `critique` | Design effectiveness feedback |
| `audit` | Severity-ranked interface findings |
| `polish` | Before/after quality pass |
| `clarify` | Copy and terminology improvements |
| `harden` | Edge-case and resilience fixes |
| `adapt` | Context and device adaptation |
| `distill` | Removed complexity and simplified flow |
| `amplify` | Controlled expressive adjustment |
| `extract` | Reusable components, tokens, and patterns |
| `motion` | Motion decision and review table |

## Add-A-Skill Rule

Add a new public skill only when it introduces a new work mode that cannot be
cleanly expressed as a mode or reference inside an existing skill.
