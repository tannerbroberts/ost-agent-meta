---
type: Solution
status: unvalidated
source: >-
  founder-directive:2026-07-24 — assertion-vs-trace distinction, stated in
  session
created: '2026-07-25'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A trace of calls, outcomes and durations carries the defects a session actually had]]

**The idea.** Instrument the single tool-dispatch choke point (buildOstTools) so every allowlisted invocation appends one JSONL event — tool, outcome, duration, surface, input size, never content — to `.ost-agent/usage/events.jsonl` inside the vault. A `usage` adapter rolls each finished day into one evidence item of computed statistics. Fail-open: telemetry may lose an event, never a mutation.

**Contrast with siblings:** the reconciler (sibling) consumes this trace to test the narrative; the transcript-derived sibling gets similar data with zero new instrumentation but only for Claude-Code-driven sessions — this works identically for MCP, CLI, and headless pass surfaces.

**Trade-off:** counts and timings only; a defect that leaves all calls green (like the 2026-07-24 evidence-strip) is invisible to the trace without diff-awareness. That limit is exactly what this solution's assumption test probes.

## Build
Shipped 2026-07-24 at the operator's direction (repo commit 711898a: src/telemetry/usage.ts, src/adapters/usage.ts, 10 new tests, 186/186 passing, enabled by default). Built human-directed, outside this tree's ideate-then-test cadence — the evidence-debt gate would have blocked it; the human disposed otherwise. Status stays unvalidated until its assumption test shows the rollup carries decision-changing signal.

## Definition of done

[[Replay the hard-fix session's trace against its known defects]]

```
npx vitest run test/telemetry/trace-defect-replay.test.ts
```

Green means the trace retains enough that the hard-fix session's known defects are visible in it — the standard a trace has to meet to be worth its storage. It does not settle the defects nobody has named: a replay scored against known defects cannot report what the trace would have missed.

## History
- 2026-08-05 unlinked [[Replay the hard-fix session's trace against its known defects]] — moved under [[A trace of calls, outcomes and durations carries the defects a session actually had]] — the belief this test measures now has a node of its own
