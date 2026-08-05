---
type: Solution
status: unvalidated
source: 'agent:P3_ideate'
created: '2026-07-24'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Knowing what was already ruled out changes what an ideation pass produces]]

A durable record of every solution considered, every test proposed or run, what it cost, and what happened — consulted before ideating, so the agent stops re-proposing what has already been ruled out and can say "we tried this in March, here is what we learned."

**How it differs from its siblings:** carries *negative* knowledge, which nothing else in the tree preserves — dead ends are exactly what disappears between runs. Re-synthesis reshapes what is there; the ledger keeps what was removed.

**Trade-off:** a long ledger can freeze exploration, treating a stale failure as a permanent verdict when conditions have changed.

**Riskiest assumptions to test:** that consulting prior attempts changes what the agent proposes (feasibility); that a human finds "already tried" recall valuable enough to maintain (desirability).

Status: agent-originated candidate. Unvalidated.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked [[Paired ideation run with and without the ledger]] — moved under [[Knowing what was already ruled out changes what an ideation pass produces]] — the belief this test measures now has a node of its own

## Test

[[Paired ideation run with and without the ledger]]

`npx vitest run test/loop/attempt-ledger-repeat-rate.test.ts`

Green when the ledger-informed run proposes materially fewer solutions duplicating what the ledger records. Read it beside the absolute count of novel solutions — a ledger that suppresses repeats by making ideation timid scores well here and is a worse product. The similarity rule must be committed before the run, not tuned to produce the gap.
