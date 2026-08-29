---
type: AssumptionTest
source: 'agent-run:unattended-sweep-2026-08-29'
created: '2026-08-29'
evidence: assertion
threshold: >-
  at least 3 figures are reported for the bucket — actionable, labelled-parked
  and defaulted-parked
instrument: npx vitest run test/mcp/instrument-bucket-split.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** It is a fixture vault and an assertion about the shape of a response; nobody is the measurement.

**What the spec must assert.** Seed a fixture vault with three solutions whose tests are prose only: one whose test carries an explicit `humans-required` lane, one whose test carries an explicit `compute-only` lane, and one whose test carries no lane at all. Call `computeNextWork` and assert three distinct figures come back for the instrument bucket — actionable, labelled-parked, defaulted-parked — and that the unlabelled solution lands in the third rather than the second. Then assert the failure this is really guarding: that the response never reports a single parked total that would make the unlabelled one indistinguishable from the deliberately-labelled one.

**Why the third figure is the assertion that matters.** A two-column split is the obvious build and it would pass a two-column spec while reproducing the exact misreading the parent opportunity records — the operator concluding 65 entries were judged when most were merely defaulted by `CAUTIOUS_LANE`. A spec that only checks "two numbers came back" would go green on the wrong build.

**Why it fails today, stated honestly.** `test/mcp/instrument-bucket-split.test.ts` does not exist, so this will be filed `no-spec` and mints no permit. That is the weakest form of red and this surface cannot do better — it cannot author a spec file. The fixture shape and the three assertions above are what make the eventual red specific to this question.

**What a green would NOT settle.** Whether the operator budgets compute differently once they see three numbers instead of one. That is the desirability half and this test says nothing about it; the parent solution's own prose concedes the queue does not shrink under this candidate at all.
