---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: At least 4 of 5 runs are bounded correctly from the history alone.
instrument: npx vitest run test/loop/run-boundary-from-history.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that one run's commits can be separated from everything else in the log. Distinguishing them from a concurrent run's, or from a human's, is not obviously solvable from git alone — and the tree already carries an open question about whether a pass can tell a human edit from its own.

**Risk category: feasibility.**

**Design.** Pick five past runs whose true extent is known from other records. Give a second person only the commit history and ask them to mark where each run began and ended, using nothing but what git holds. Compare against the known answer.

**Why it is small.** The history exists and the exercise is reading it. The known extents come from journals and session records already captured.

**What it will not cover.** A person doing this by eye may use cues a program could not, so success here is an upper bound on what an automated reconstruction would achieve rather than a prediction of it.

A human runs this and records the result.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/loop/run-boundary-from-history.test.ts — Measures whether a run's first and last commit can be recovered from the auto-commit log alone, with no self-report to lean on, and whether concurrent or human commits can be excluded from the span. It fails today because nothing in the repository derives run boundaries from git — the solution's own body says the bound is exactly what is missing and that separating one run's commits from a concurrent run's is not obviously solvable from git alone. That unsolved separation is what the spec asserts, so it goes green only once the bounding exists.
