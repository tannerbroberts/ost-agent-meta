---
type: Solution
status: unvalidated
evidence: assertion
source: 'agent:P3_ideate'
created: '2026-07-24'
---
#Solution #unvalidated #evidence/assertion
[[Thirty-day log sample for existing signal]]

Derive friction from machine records instead of prose: failed tool calls, retried operations, validation rejections, abandoned passes, time-to-complete per process, commits reverted. Aggregate across runs and surface the recurring ones.

**How it differs from its siblings:** fully objective and comparable over time — counts rather than narratives — and it carries no transcript-privacy exposure. It cannot see conceptual confusion that never produced an error.

**Trade-off:** measures what happens to fail loudly, which is not the same as what is hard; silent wrong turns are invisible to it.

**Riskiest assumptions to test:** that the logs already contain enough signal without new instrumentation (feasibility); that error frequency correlates with anything a human would prioritise fixing (desirability).

Status: agent-originated candidate. Unvalidated.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
