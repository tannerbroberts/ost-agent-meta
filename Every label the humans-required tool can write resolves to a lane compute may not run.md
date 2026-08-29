---
type: AssumptionTest
source: 'agent-run:unattended-sweep-2026-08-29'
created: '2026-08-29'
evidence: assertion
threshold: zero of the labels the tool can write resolve to computeMayRun true
instrument: npx vitest run test/knowledge/humans-required-is-one-way.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** The whole question is what a function returns for a set of inputs already on disk; no person is the measurement.

**What the spec must assert, so the red is about this question rather than about a missing file.** Drive the humans-required write path over every input it accepts — including the adversarial ones, since fail-closed is the property under test: a lane id it was not given, an empty string, `undefined`, and a caller passing `compute-only` directly. For each, assert the lane the node ends up carrying satisfies `computeMayRun(lane) === false`. Then assert the complement, which is the half a lazy spec would skip: that no code path in the tool reaches a label for which `computeMayRun` is true — enumerate `LANES`, filter to `computeMayRun === true`, and assert the tool refuses every one of them by name rather than trusting that it happens not to be called with them.

**Why it fails today, stated honestly.** `test/knowledge/humans-required-is-one-way.test.ts` does not exist, so this run will be filed `no-spec` and will mint no build permit — the weakest reason a command can fail, and the one this pass cannot avoid, because authoring a spec file is not something this surface can do. The paragraph above is the repair: it names the module (`src/knowledge/lanes.ts`), the exported predicate (`computeMayRun`), the constant (`LANES`) and the four adversarial inputs, so the builder's first act is writing an assertion rather than deciding what the test was about. The moment that file exists with those assertions in it, the red becomes specific to this question.

**What a green here would NOT settle.** That anyone wants the grant. This is feasibility only: it says the mechanism is as narrow as the solution claims, and says nothing about desirability, viability or usability. The sibling assumption's test is where the wanting is asked about, and it needs a person.
