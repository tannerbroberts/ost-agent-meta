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

## What a green run does not settle

The measurement is retrospective and the dependency model is reconstructed, which means it answers "how much work *appears* independent of the block, viewed afterwards, by a model we wrote". A run in the moment does not have that view. Some of what the walk counts as independent would have looked entangled from inside the pass, and banking it would have required a confidence the run did not have.

It also counts work, not value. Ten blocked runs might each leave a large volume of trivial work available and nothing that mattered, and the count cannot tell — a high number is compatible with banking the block being pointless.

And it says nothing about the failure that makes this solution risky rather than merely unhelpful: work carried out under an assumption the block would have corrected. Every unit the walk counts as safely independent is safe only if the answer to the blocking question could not have changed it, and a dependency model built from transcripts cannot see a dependency the transcript never made explicit.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/loop/blocked-run-independent-work.test.ts` — No test files found, exiting with code 1
- 2026-08-17 **green** (exit 0) `npx vitest run test/loop/blocked-run-independent-work.test.ts` — Duration  221ms (transform 19ms, setup 0ms, collect 19ms, tests 1ms, environment 0ms, prepare 28ms)
