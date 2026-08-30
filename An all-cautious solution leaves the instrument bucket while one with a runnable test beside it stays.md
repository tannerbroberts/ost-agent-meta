---
type: AssumptionTest
source: 'agent-ideation:2026-08-30-unattended-sweep'
created: '2026-08-30'
evidence: assertion
threshold: >-
  0 solutions carrying a compute-runnable test are dropped, and at least 1
  all-cautious solution is
instrument: npx vitest run test/eval/lane-aware-instrument-bucket.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**The design.** Build a fixture tree with three solutions and run `solutionsMissingInstruments` over it. The first carries two tests, both `humans-required`, neither with an instrument — it must not be listed. The second carries two tests, one `humans-required` and one in a lane `computeMayRun` allows — it must still be listed, because a live path to a builder exists beneath it and a filter keyed on "any" rather than "every" would lose it. The third carries two tests with no lane field at all — the case the assumption names as the second way this goes wrong, since `computeMayRun` fails closed on a missing lane and would silently drop every pre-lanes solution in the tree. The spec asserts which of the three come back and pins the unlabelled case explicitly rather than letting it ride on the cautious default.

**Pre-committed bar, stated before running:** 0 solutions carrying a compute-runnable test are dropped, and at least 1 all-cautious solution is. A filter that drops nothing has not been built; a filter that drops the second solution is worse than no filter and the candidate should be refused rather than fixed, because losing a buildable solution silently is the failure the bucket exists to prevent.

**What kind of red this is, said plainly rather than left for the log to reveal.** `test/eval/lane-aware-instrument-bucket.test.ts` does not exist, so this command is red today for the weakest available reason — it would be equally red under any question written on that filename, and `runInstrument` will file it as `no-spec` rather than as a measurement. That is the strongest red this surface can author: writing the failing assertion requires a write grant on the product repository, which an unattended sweep does not hold and should not. The pre-committed bar above is what carries the builder across that gap, and it is doing real work here rather than filling a field — `confirmPermit` keeps a weak red's permit only when the threshold is bound, on the precedent of one complete lifecycle this vault watched succeed that way.

**What a green here does not settle.** Only that the filter behaves as specified against a fixture. It says nothing about whether the lanes on this vault's 488 real tests were set by anyone's judgement — the candidate that distrusts the bare field is built on exactly that doubt, and this spec is blind to it. It also says nothing about desirability or viability: nobody outside this project has been asked whether a quieter bucket is what they want.
