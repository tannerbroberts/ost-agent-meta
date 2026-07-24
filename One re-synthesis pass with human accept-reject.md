---
type: AssumptionTest
status: unvalidated
source: 'agent:P4_assumptions'
created: '2026-07-24'
---
#AssumptionTest #unvalidated #desirability

**Assumption under test (desirability, with a harm check):** Restructuring proposals are ones a human accepts — and none of them would have quietly destroyed meaning if applied automatically.

**Proposed test:** Run one re-synthesis over the tree as it stands after this pass. Every output is a proposal, applied to nothing. A human marks each accept / reject, and separately flags any proposal that would have lost information had it been auto-applied.

**Size:** one pass of compute plus an hour of review, against the current 33 nodes.

**Pre-committed threshold:** ≥50% of proposals accepted AND zero proposals flagged as meaning-destroying. The second condition is absolute — one silent loss of meaning means re-synthesis stays proposal-only forever, whatever the accept rate.

**Decides:** whether compression can ever run unattended, or only ever as a suggestion to a human.

Proposed by the agent — a human accepts or rejects; nothing is applied by the agent. No results recorded here.
