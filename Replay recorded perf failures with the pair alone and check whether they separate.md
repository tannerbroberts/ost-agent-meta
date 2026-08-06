---
type: AssumptionTest
status: unvalidated
created: '2026-08-06'
evidence: assertion
threshold: >-
  The measurement-and-criterion pair alone correctly labels at least 8 of 10
  fixture failures as noise or regression.
instrument: npx vitest run test/eval/perf-gate-noise-band.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** The question is whether two numbers carry a distinction, and that is settled by feeding the numbers to a rule, not by asking anyone.

Build a fixture of recorded perf-gate failures with the cause already known — some produced by a deliberate slowdown committed on purpose, some produced by running the same unchanged commit while the machine was loaded. Present each to the classifier as only what this solution renders: the measurement and the criterion. Require it to label each.

Then repeat with the spread included — the min and max the same commit produces across repeated runs — and compare the two separation rates. That comparison is the actual finding. If the pair alone separates the fixture, the parent assumption holds and the solution is right as titled. If the pair does not and the triple does, the assumption is false in the specific way that names the fix, and this solution should be rewritten to carry the band rather than abandoned.

**Pre-committed bar:** the pair alone correctly labels at least 8 of 10 fixture failures. Below that, the pair is insufficient and the node gets rewritten around the spread.

Deliberately not a threshold on the triple: this test exists to falsify the pair, and setting a second bar would invite reporting whichever one passed.

**What a green run here does not settle.** It measures separation against a fixture whose causes are known because they were manufactured. Real failures arrive without labels, and a classifier that is right about ten constructed cases may be useless on the eleventh real one. It also says nothing about whether an operator reading the rendered pair reaches the same conclusion the classifier does — the sibling solution "Three gates fired correctly in one session and every one of them read as noise first" is about exactly that gap, and no exit code closes it.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/eval/perf-gate-noise-band.test.ts` — No test files found, exiting with code 1
