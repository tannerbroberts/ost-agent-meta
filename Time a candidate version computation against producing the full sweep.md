---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  A candidate costs under 10% of producing the sweep and detects 20 of 20
  changes.
instrument: npx vitest run test/ost/sweep-version-cost.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that a version can be both cheap and honest. If deriving it costs as much as producing the sweep, nothing is saved; if it is cheap but coarse, a caller will be told it is current when it is not, which is worse than re-reading.

**Risk category: feasibility.**

**Design.** Implement two candidate versions — one over file modification times, one over content hashes — and time each against producing the full sweep on this vault, which now holds several hundred nodes. Then make twenty representative changes and check whether each candidate detects every one.

**Why it is small.** Two small functions and a timing loop over a vault that already exists at realistic size.

**What it will not cover.** Timing on one vault at one size. The cheap candidate's cost may grow differently from the sweep's as the tree gets larger, so the ratio matters more than either number.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/ost/sweep-version-cost.test.ts — Every clause of this node's threshold is a number a command produces: "A candidate costs under 10% of producing the sweep and detects 20 of 20 changes." The spec implements both candidate versions the design names — one over file modification times, one over content hashes — times each against a full sweep of this vault at its present several-hundred-node size, asserts the ratio under the 10% bar, then applies twenty representative mutations (a new node, an appended section, a retitled file, a removed edge, a status change, and so on) and asserts every candidate detects all twenty. It fails today because the sweep returns no version at all: `ost_next_work` recomputes the outstanding list from scratch on every call and hands the caller nothing to compare against, so there is no cheap candidate to time and no change-detection to score. This is the one test under this solution whose answer decides whether the solution is worth building, because a version that is cheap but coarse tells a caller the tree is current when it is not, which is worse than the re-reading it was meant to save. What it does not settle is scaling: the node says so itself — one vault at one size, and the cheap candidate's cost may grow differently from the sweep's, so the ratio is the finding and neither absolute number is.
