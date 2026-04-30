---
name: performance-research
description: Improve performance through workload framing, measurement, current stack-specific research, bottleneck evidence, narrow optimization, and regression guards. Use when software is slow, resource-heavy, costly, needs performance review beyond generic advice, or the user invokes performance research.
---

# Performance Research

Use this skill to improve performance without relying on remembered
optimization folklore. The durable behavior is the process: frame the workload,
measure, research the exact stack and symptom, patch the proven bottleneck, and
verify the same workload again.

## Invocation Behavior

Any invocation of performance research is a request to start the workflow, not
only to acknowledge that the skill is loaded. If the user provides context,
use that context to frame the workload first. If the user gives no specific
workload, infer one from the current codebase, documentation, issue context,
tests, benchmarks, build scripts, and likely user-facing or operational hot
paths.

Begin by gathering enough local evidence to identify the application type,
entry points, performance-sensitive surfaces, and available measurement
commands. State the inferred workload and assumption, then continue into the
baseline step. Ask a clarifying question only when local context is insufficient
to infer any meaningful workload or when measuring would require external
credentials, production data, paid services, or destructive actions.

## Vocabulary

- `Workload`: the concrete operation being optimized.
- `Budget`: the acceptable limit for latency, CPU, memory, I/O, network,
  bundle size, render count, query count, cost, or throughput.
- `Baseline`: the current measured behavior of the workload.
- `Hot path`: code or infrastructure exercised enough by the workload to matter.
- `Bottleneck`: the measured constraint limiting the workload.
- `Candidate`: a possible optimization with evidence, impact, risk, and a
  verification path.
- `Regression guard`: a benchmark, test, trace, metric, alert, query plan,
  bundle budget, or scripted check that catches backslide.

## Workflow

1. Frame the workload:
   - Identify the user-visible operation, environment, data shape, traffic
     pattern, runtime versions, and target budget.
   - If the target is vague, state a practical provisional budget before
     measuring.
2. Establish a baseline:
   - Use the repo's existing tests, profilers, logs, traces, browser tooling,
     benchmarks, query plans, or small harnesses.
   - Capture the exact command, scenario, input size, and result.
3. Classify the bottleneck:
   - CPU, allocation, GC, I/O, database, network, serialization, rendering,
     hydration, bundle size, cold start, lock contention, cache miss, or external
     dependency.
   - Do not choose a fix until the bottleneck class has evidence.
4. Research the exact context:
   - Look up current authoritative guidance for the language, runtime,
     framework, database, browser, cloud service, library, and version involved.
   - Prefer official docs, changelogs, runtime guides, framework docs, query
     planner docs, standards, and issue trackers. Use articles only when they
     are specific, recent enough, and testable against the workload.
   - Record what was researched and which finding changed the optimization plan.
5. Present candidates:
   - Rank by expected impact, confidence, implementation risk, and
     regression-guard feasibility.
   - Do not implement broad performance rewrites until the user selects a
     candidate or the request explicitly asks for a fix.
6. Patch narrowly:
   - Change the proven bottleneck or the smallest caller/data-shape needed to
     remove it.
   - Preserve correctness, observability, accessibility, and freshness semantics.
7. Verify:
   - Re-run the original baseline scenario.
   - Compare before and after using the same workload.
   - Add or recommend the strongest feasible regression guard.

## Candidate Format

```markdown
| Candidate | Evidence | Research finding | Expected impact | Risk | Verification |
| --- | --- | --- | --- | --- | --- |
```

## Guardrails

- No performance claim without a baseline or an explicit measurement gap.
- No generic best-practice patch unless it targets the measured bottleneck.
- No microbenchmark unless it represents the workload's hot path.
- No caching proposal without invalidation, freshness, and capacity rules.
- No database advice without inspecting query shape, indexes, cardinality, or
  query plans when available.
- No frontend speed claim without checking the relevant layer: network, bundle,
  parsing, hydration, rendering, layout, main-thread work, or asset loading.
- No concurrency or batching change without preserving ordering, cancellation,
  backpressure, retry, and failure semantics.
- No tradeoff against correctness, security, accessibility, or observability
  unless the user explicitly accepts it.

## Output

- `Workload`
- `Budget`
- `Baseline`
- `Bottleneck evidence`
- `Research notes`
- `Optimization candidates`
- `Patch`
- `Verification`
- `Regression guard`
- `Residual risk`
