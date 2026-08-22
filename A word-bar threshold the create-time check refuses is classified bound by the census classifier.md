---
type: AssumptionTest
status: unvalidated
source: 'agent-ideated:2026-08-22-unattended-sweep'
created: '2026-08-22'
evidence: assertion
threshold: >-
  All 3 word-bar threshold strings classify `bound` under thresholdKindOf, and
  the create-time guard refuses at least 2 of the 3.
instrument: npx vitest run test/eval/create-time-bar-parity.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**What this settles.** Whether the two readers of a threshold string disagree. Take threshold strings that state a real bar in words rather than digits — "at least five of twenty book a kickoff", "no fewer than three of ten sessions recover", "exactly one entrypoint runs the bundle without building it" — and run each through both readers: the create-time numeric-bar guard that `ost_create_node` applies to a no-spec instrument, and `thresholdKindOf` from `src/eval/coverage.ts`, which is what the rollup's fixed-bar line and `confirmPermit`'s `thresholdBound` both consult.

**Pre-committed threshold:** all 3 word-bar strings classify `bound` under `thresholdKindOf`, and the create-time guard refuses at least 2 of the 3. Agreement on all 3 refutes the assumption; disagreement on 2 or more supports it.

**Why the spec fails today.** No spec asserts parity between these two readers, because nothing in the repository treats them as one contract — `test/eval/unfixed-thresholds.test.ts` exercises the census side alone and `test/ost/instrument.test.ts` exercises the create-time side alone, and neither feeds the other's input through both. The named spec has to construct the shared string set and assert the two verdicts against each other, which is behaviour that does not exist.

**Stated so it is not over-read: this is a no-spec red.** The file named below has not been written, so today it fails for the reason any unwritten file fails. It carries a bound bar above, which is what makes it a working build permit rather than a vacuous one, and the builder's job is to write the parity spec and make its assertions decide the question.

**What a green here does NOT settle.** Nothing about whether the guard should be dropped. Establishing that the guard produces false refusals leaves the operator's risk call — "Ask the operator, with the 2026-08-09 vacuous-red count in hand, whether the write-time numeric-bar check may be relaxed" — exactly where it was. Feasibility answered mechanically; desirability and viability untouched.

**Category:** feasibility.
