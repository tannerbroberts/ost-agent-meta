---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  In at least 6 of 10 runs, half or more of the steps are independent of any
  credentialed step.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that a useful amount of a run's work is independent of its credentialed steps. If most of what a run does sits downstream of one push or one authenticated read, reordering buys nothing and the run still ends with almost nothing accomplished.

**Risk category: feasibility.**

**Design.** Take ten completed runs from the journals. Classify every step as needing the operator's credential or not, and build the dependency order. Compute, per run, what fraction of the steps could have been completed before the first credentialed step blocked anything downstream of it.

**Why it is small.** Analysis of records that already exist, no build, and it produces a distribution rather than an anecdote.

**What it will not cover.** Past runs were written by an agent that stopped at the first block, so their step order reflects that habit. A run designed to defer credentialed work might sequence itself quite differently, and this cannot see that counterfactual.
