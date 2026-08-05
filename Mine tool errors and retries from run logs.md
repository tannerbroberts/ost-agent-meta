---
type: Solution
status: unvalidated
source: 'agent:P3_ideate'
created: '2026-07-24'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The existing logs already contain enough friction signal to be worth aggregating]]

Derive friction from machine records instead of prose: failed tool calls, retried operations, validation rejections, abandoned passes, time-to-complete per process, commits reverted. Aggregate across runs and surface the recurring ones.

**How it differs from its siblings:** fully objective and comparable over time — counts rather than narratives — and it carries no transcript-privacy exposure. It cannot see conceptual confusion that never produced an error.

**Trade-off:** measures what happens to fail loudly, which is not the same as what is hard; silent wrong turns are invisible to it.

**Riskiest assumptions to test:** that the logs already contain enough signal without new instrumentation (feasibility); that error frequency correlates with anything a human would prioritise fixing (desirability).

Status: agent-originated candidate. Unvalidated.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked "Thirty-day log sample for existing signal" — moved under "The existing logs already contain enough friction signal to be worth aggregating" — the belief this test measures now has a node of its own

## Proving this

"Thirty-day log sample for existing signal"

```
npx vitest run test/telemetry/log-only-friction-recall.test.ts
```

Red today: the trace is rolled up only into daily per-tool counts. Nothing derives recurring friction classes from it, and nothing compares that derivation against the friction the transcript channel already found, so there is no recall figure to assert against. Green when the log-only derivation exists and can be scored against a known set.

**What a green run would not settle.** It answers the feasibility half — the logs hold enough signal — and leaves this node's own stated trade-off untouched: machine records measure what fails *loudly*, and the silent wrong turns are invisible to them by construction. It also says nothing about the desirability assumption written into this node, that error frequency correlates with what a human would actually prioritise fixing. That one needs a person ranking the output.
