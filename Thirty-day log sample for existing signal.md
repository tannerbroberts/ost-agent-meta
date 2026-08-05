---
type: AssumptionTest
status: unvalidated
source: 'agent:P4_assumptions'
created: '2026-07-24'
evidence: assertion
instrument: npx vitest run test/telemetry/log-only-friction-recall.test.ts
---
#AssumptionTest #unvalidated #feasibility #evidence/assertion

**Assumption under test (feasibility):** The records that already exist — tool errors, retries, validation rejections, abandoned passes, commit history — contain enough signal to work with, without adding instrumentation first.

**Proposed test:** Sample the last thirty days of existing logs and history by hand. Count distinct recurring failure patterns and check whether each maps to something a human would call a product problem.

**Size:** a few hours against data already on disk; nothing to build, nothing to wait for.

**Pre-committed threshold:** ≥3 recurring patterns found AND ≥2 of them map to a product problem a human agrees is worth fixing. Fewer means instrumentation is a prerequisite, which changes the cost of this option entirely.

**Decides:** whether log mining is the cheap channel it looks like, or a build project in disguise.

Proposed by the agent — a human judges the mapping to product problems. No results recorded here.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 instrument: (none) → npx vitest run test/telemetry/log-only-friction-recall.test.ts — Takes a thirty-day window of the machine trace and measures what share of the friction already known from the transcript channel is recoverable from failed calls, retries and validation rejections alone — the node's stated feasibility assumption, that the logs hold enough signal without new instrumentation. It fails today because the trace is only rolled up into daily counts by tool; nothing derives recurring friction classes from it or compares that derivation against a known set, so there is no recall figure for the spec to assert against.
