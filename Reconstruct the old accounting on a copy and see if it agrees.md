---
type: AssumptionTest
source: 'agent:ideation-2026-08-03'
created: '2026-08-03'
evidence: assertion
threshold: >-
  Reconstruction agrees with ost-agent@0.1.3's own answer on at least 26 of the
  27 items, with zero items marked done that the old build called outstanding.
instrument: npx vitest run test/ost/accounting-reconstruction.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility.** A migration is a guess about the past — it infers a fact the old build never wrote down. This test asks whether that inference is recoverable at all, and it can be answered exactly, because the original disagreement is reproducible: the same vault read 9 outstanding under one build and 27 under another.

**The test.** On a copy, run the reconstruction against the vault state that produced the 9-versus-27 split, and compare its output item by item against what `ost-agent@0.1.3` actually reported. No new judgement is needed — the old build is the oracle, and it can still be run.

**Why the second condition matters more than the first.** The two error directions are not equal. Marking something outstanding that was done costs a wasted pass. Marking something done that was not costs a silently dropped piece of work, permanently, in an append-only store. So the threshold tolerates one miss in the safe direction and none in the dangerous one.

**Why this is the right first test for this row.** All three siblings depend on being able to tell that a vault was written under different accounting, but only this one depends on being able to *reconstruct* it. If reconstruction fails, the row's answer is "Keep reading the legacy signal as a fallback so old work still counts" or "Report the accounting change explicitly instead of folding it into the counts", and no further work on migration is warranted — so this test is also the cheapest way to eliminate an option.

**A live case to include:** the Issues section on this opportunity records `.ost-agent/state/mapped.json` listing two TRANSCRIPT ids as mapped while `ost_next_work` called both outstanding in the same minute. Whatever reconstruction is built should be checked against that pair too, since it is the same disagreement happening now rather than historically.

Proposed, not run. Recording a result is a human's `ost-agent result`.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/ost/accounting-reconstruction.test.ts — The node names a reproducible oracle — `ost-agent@0.1.3`'s own answer on the vault state that produced the 9-versus-27 split — so the spec runs the reconstruction against that committed state, compares item by item against the old build's recorded output, and asserts agreement on at least 26 of 27 with zero items marked done that the old build called outstanding. It fails today because no reconstruction exists.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/ost/accounting-reconstruction.test.ts` — No test files found, exiting with code 1
