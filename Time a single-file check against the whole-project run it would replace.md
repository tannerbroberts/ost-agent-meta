---
type: AssumptionTest
source: 'TRANSCRIPT:b7aae32d-150a-462f-9027-cdf7af12badd'
created: '2026-08-04'
evidence: assertion
threshold: >-
  A single-file check over `src/security/tools.ts` reports the TS2339 on
  `configProblem` and returns in under 2 seconds, while the whole-project `tsc
  --noEmit` it replaces takes longer than 10 seconds on the same machine.
instrument: npx vitest run test/runner/incremental-typecheck.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Category: feasibility, and the cost half of it specifically.** This solution's whole risk is speed. Nobody doubts a narrow typecheck can find the error; the open question is whether it can find it fast enough that a run will tolerate it on every edit. A check that costs five seconds per write will be disabled, and a disabled check is worse than an unbuilt one because the tree will record it as tried.

**Lane: compute-only.** Both halves are timings taken from committed code.

**Why the bar names both numbers.** An absolute threshold alone would fail on a loaded machine for reasons that have nothing to do with the design — the same confusion the tree already carries as a separate need. Requiring the single-file check to beat the whole-project run by a wide margin *on the same machine in the same run* makes the comparison self-normalising, so a busy machine slows both and the verdict holds.

**What a green run does NOT settle.** It settles that the check is fast and finds the known error. It does not show that per-edit checking changes any outcome — a run might absorb the diagnostic and carry on exactly as it did before — and it says nothing about the false-positive rate mid-refactor, which is the failure most likely to make this unbearable in practice. That one needs a real batch of edits observed end to end, not a timing.

## Definition of done

`npx vitest run test/runner/incremental-typecheck.test.ts`

Red today: the spec file does not exist and no per-file check path is implemented.

## Instrument Log
- 2026-08-07 **red** (exit 1) `npx vitest run test/runner/incremental-typecheck.test.ts` — No test files found, exiting with code 1
