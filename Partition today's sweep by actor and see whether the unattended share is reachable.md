---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  The nobody-may-act bucket is empty, or every item in it has a named reason a
  human accepts.
instrument: npx vitest run test/ost/sweep-actor-partition.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that partitioning produces a share an unattended pass can actually finish. If the pass's own partition still contains items no actor may resolve — the eighteen unmappable evidence records among them — the split changes the presentation and not the problem.

**Risk category: feasibility.**

**Design.** Take the current sweep and partition every item by who may act: unattended pass, attended session, human only, nobody. The fourth bucket is the finding. If it is empty, the split works; if the eighteen stranded items land there, the partition has located the problem without solving it.

**Why it is small.** One sweep, one classification pass, no build.

**What it will not cover.** It cannot say whether a pass seeing only its own share would lose sight of what it is blocked behind. That risk — a loop reporting done while the human partition grows unread — needs watching over time rather than a single classification.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/ost/sweep-actor-partition.test.ts — The finding this test is written for is a bucket count over the sweep the tool already computes, so the classification needs no person: the spec partitions every item `ost_next_work` returns by who may act on it — unattended pass, attended session, human only, nobody — and asserts the fourth bucket is empty, or that every item in it carries a named reason. It fails today because nothing partitions the sweep by actor at all; there is no actor field on a sweep item and no classifier to produce one. The node predicted the stranded evidence records would land in the fourth bucket, and the 2026-08-05 pass confirms the prediction from the other direction: twenty-two evidence items corroborated needs the tree already holds and no actor on any surface could clear them, because clearing requires a node citing the item as `source`. Note the limit the node states and this does not touch: whether a human accepts a given reason is a human's call, and the spec asserts a reason is present, never that it is good.
