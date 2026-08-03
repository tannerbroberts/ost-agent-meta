---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  Between 2 and 6 of 10 diverge, and the operator calls at least 7 of 10 worth
  being asked.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that this produces a usable signal — that divergence between the operator's answer and the agent's is measurable, and that its rate says something about whether the operator still understands their tree.

**Risk category: feasibility.**

**Design.** On ten occasions across a month, the agent picks a fork, writes down its own answer without showing it, and asks the operator. Record both answers and whether they agree. Also record how long the operator took and whether they said the question was worth being asked.

**Why it is small.** Ten questions over a month, each a minute, and it needs nothing built beyond withholding an answer that already exists.

**What it will not cover.** Divergence has two causes — the operator drifting, or the agent being wrong — and a rate alone cannot separate them. Whether the divergences were the operator being right is the more interesting question and needs a third party to judge.

The operator must agree to be asked before this runs. A human runs it and records the result.
