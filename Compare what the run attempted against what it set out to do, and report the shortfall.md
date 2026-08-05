---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Have a blind reader sort ten shortfall reports into justified and evasive]]

The run states its intended scope at the start, before it knows whether the gate will be difficult. At the end, what it actually attempted is compared against that statement and the difference is reported — not as a failure, but as a fact printed next to the result. A pass earned by attempting less arrives with the narrowing written beside it.

The timing is the mechanism. A scope declared before the obstacle is known cannot be shaped by the obstacle, and that is the only thing that makes the comparison meaningful.

**Compared to the alternatives.** Costs nothing, blocks nothing, and works when no human is present — which neither of the other two can claim. It also has no teeth: it produces a report, and a report can be ignored or explained away. Recording scope on the gate refuses the pass outright; requiring a human to change scope prevents the narrowing entirely. This one only makes it visible.

**What would make this the wrong pick.** Narrowing is often correct. A run that reasonably drops a branch after learning it was irrelevant will produce the same shortfall as one that dropped it to get past a gate, and a report that cannot distinguish them will be read as noise within a fortnight.

## Definition of done

[[Have a blind reader sort ten shortfall reports into justified and evasive]]

`npx vitest run test/loop/scope-shortfall.test.ts`

The spec asserts the timing, because the node is explicit that the timing *is* the mechanism: intended scope is recorded at run start, immutable once the gate is known, and the end-of-run shortfall is diffed against that recorded declaration rather than a restated one. A scope that can be edited after the obstacle appears makes the comparison meaningless, so immutability is the load-bearing assertion. Red today because nothing declares scope at the start of a run.

**What a green here does not settle, and the node names it precisely.** Narrowing is often correct. A run that reasonably drops a branch after learning it was irrelevant produces the same shortfall as one that dropped it to get past a gate, and no spec distinguishes them — that is exactly what the blind reader is being asked to do. The node's other admission stands too: this has no teeth. It produces a report, and a report can be ignored or explained away, which a passing suite does nothing about.
