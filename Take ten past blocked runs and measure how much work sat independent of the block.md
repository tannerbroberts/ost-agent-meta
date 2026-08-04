---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  In at least 6 of 10 runs, half or more of the remaining work was independent
  of the block.
instrument: npx vitest run test/loop/blocked-run-independent-work.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that a blocked run has other work available. If most of what the run intended sits downstream of the block, there is nothing to carry on with, and the operator now learns about it later than they would have.

**Risk category: feasibility.**

**Design.** Find ten past runs that stopped at something only the operator could do. For each, reconstruct what it still intended to do and classify each remaining item as dependent on the blocked step or not. Compute the share that was independent.

**Why it is small.** The journals and session records hold both the intent and the stopping point.

**What it will not cover.** Reconstructing intent after the fact is imprecise, and a run that expected to stop may not have planned far beyond the block. The estimate will tend to understate available work.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/loop/blocked-run-independent-work.test.ts — The ten runs are captured transcripts already on disk, so the measurement is a dependency walk over each one — reconstruct what was outstanding at the moment of the block and count how much of it needed nothing the block was waiting on; it fails today because no dependency model of a pass's outstanding work exists to walk.
