---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  Raw measurement varies by more than 50% across load levels while the ratio
  varies by under 10%.
instrument: npx vitest run test/eval/calibration-ratio-stability.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that the calibration workload degrades the same way the real one does under load. That holds for CPU-bound work and much less well once disk or network is involved — and if the two respond differently, the ratio drifts for reasons unrelated to the code, which is worse than a wrong absolute number because it is unpredictable.

**Risk category: feasibility.**

**Design.** Run the gate and its calibration together at four load levels, from idle to heavily contended, with the code unchanged throughout. Record the raw measurement and the ratio at each level. The raw number should move substantially; the ratio should not.

**Why it is small.** One afternoon, one machine, no code changes to the thing being measured.

**What it will not cover.** One machine and one kind of induced load. Contention from disk behaves differently from contention from CPU, and a laptop under thermal throttling differently again.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/eval/calibration-ratio-stability.test.ts — The threshold is two numeric clauses over measurements the spec takes itself — raw measurement varies by more than 50% across load levels while the ratio varies by under 10% — so the spec runs the gate and its calibration together at four induced load levels with the code unchanged, records both at each level, and asserts the raw spread exceeds 50% while the ratio spread stays under 10%. It fails today because no calibration run exists and the gate has no ratio to compute.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/eval/calibration-ratio-stability.test.ts` — No test files found, exiting with code 1
