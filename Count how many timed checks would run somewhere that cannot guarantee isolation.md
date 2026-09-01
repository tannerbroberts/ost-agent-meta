---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: At least 50% of timed-check runs happen somewhere isolation can be guaranteed.
instrument: npx vitest run test/release/timed-check-isolation-share.test.ts
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that enough of the timed checks would still gate somewhere. If most runs happen where isolation cannot be promised, nearly every check becomes advisory — and an advisory number that cannot fail anything gets scrolled past for months while the regression it watched for arrives.

**Risk category: viability.**

**Design.** Enumerate every place a timed check currently runs: local laptop, CI, scheduled pass, a contributor's machine. For each, determine whether load could be controlled, and weight by how often checks actually run there. Compute the share of runs that would remain gating.

**Why it is small.** A census against the CI configuration and the run records, no build.

**What it will not cover.** It counts runs, not importance. The one place isolation is impossible might be where regressions are most likely to be introduced, and a share alone will not show that.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/release/timed-check-isolation-share.test.ts — Censuses every place a timed check runs — local machine, CI, scheduled pass, contributor machine — determines for each whether load can be controlled, weights by how often checks actually run there from the run records, and asserts at least half of runs would remain gating. It fails today because nothing enumerates the run locations or joins them to the run-frequency records.

## Instrument Log
- 2026-08-04 **red** (exit 1) `npx vitest run test/release/timed-check-isolation-share.test.ts` — No test files found, exiting with code 1
- 2026-09-01 **green** (exit 0) `npx vitest run test/release/timed-check-isolation-share.test.ts` — Duration  310ms (transform 25ms, setup 0ms, collect 30ms, tests 71ms, environment 0ms, prepare 31ms) [spec 3563764fdfb9]
