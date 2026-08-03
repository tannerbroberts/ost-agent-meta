---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  A candidate costs under 10% of producing the sweep and detects 20 of 20
  changes.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that a version can be both cheap and honest. If deriving it costs as much as producing the sweep, nothing is saved; if it is cheap but coarse, a caller will be told it is current when it is not, which is worse than re-reading.

**Risk category: feasibility.**

**Design.** Implement two candidate versions — one over file modification times, one over content hashes — and time each against producing the full sweep on this vault, which now holds several hundred nodes. Then make twenty representative changes and check whether each candidate detects every one.

**Why it is small.** Two small functions and a timing loop over a vault that already exists at realistic size.

**What it will not cover.** Timing on one vault at one size. The cheap candidate's cost may grow differently from the sweep's as the tree gets larger, so the ratio matters more than either number.
