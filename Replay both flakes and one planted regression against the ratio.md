---
type: AssumptionTest
source: 'agent-ideated:2026-08-02-maintenance-pass'
created: '2026-08-02'
evidence: assertion
instrument: npx vitest run test/telemetry/same-run-baseline-ratio.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility.** Whether the ratio separates the two cases it must separate.

**The assumption under test.** That a same-run baseline cancels contention without also cancelling real regressions. Both halves matter and they pull against each other: a baseline that tracks the operation closely absorbs genuine slowdowns along with the noise, and a baseline that tracks it loosely fails to cancel the noise at all. The candidate is only worth building if some baseline sits in between, and nobody knows whether one does.

**The test (two known-good cases, one planted bad one).** Instrument a candidate baseline alongside the existing timing. Then produce three scenarios and record the ratio in each:

1. **Contention, no regression** — run the full 141-file suite under load, reproducing the 2026-08-01 conditions where the test failed at 2004ms and 2280ms. The ratio must stay green.
2. **Isolation, no regression** — run the test alone, where it passed at 18077ms of margin. The ratio must stay green.
3. **Planted regression** — deliberately slow `ost_next_work` by a known factor (an added pass over the node set is the realistic shape). The ratio must go red.

**Pre-committed threshold.** Green, green, red across **3 of 3 repetitions of each scenario**. Any scenario failing on any repetition closes the candidate — a timing gate that is right most of the time is the failure being fixed, not a fix for it.

**And name the factor.** A result must state the smallest planted slowdown the ratio still catches. If the answer is "only a 3× regression," the ratio is not measuring anything worth gating on, and that finding should push toward [[Assert on work units instead of milliseconds]] regardless of whether the three scenarios technically passed.

**Who runs it.** A human, or an attended session with a build environment. This pass proposes the design only.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/telemetry/same-run-baseline-ratio.test.ts — Replays the two recorded flakes and a planted regression against a same-run baseline ratio and asserts only the regression fails; fails today because the gate compares against the clock, so all three look alike.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/telemetry/same-run-baseline-ratio.test.ts` — No test files found, exiting with code 1
