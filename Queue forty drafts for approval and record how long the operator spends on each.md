---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: Median time on the last ten is at least half the median on the first ten.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that an operator facing a queue of drafts actually reads them. Faced with forty, they will approve in bulk — and bulk approval is indistinguishable from automation while feeling like oversight, which is worse than automating openly.

**Risk category: usability.**

**Design.** Present the operator with forty drafts from a real pass, one at a time, and record time spent on each and whether it was edited or rejected. Do not tell them what is being measured. Compare the first ten against the last ten.

**Why it is small.** The drafts exist — this pass alone produced far more than forty. The measurement is a timestamp per decision.

**What it will not cover.** One operator on one occasion, who knows the tree well and is unusually invested in it. Someone less invested would degrade faster, not slower, so this is close to the best case.

A human runs this and records the result.
