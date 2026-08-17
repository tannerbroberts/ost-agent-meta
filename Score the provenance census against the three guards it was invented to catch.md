---
type: AssumptionTest
source: 'agent-ideation:2026-08-06-unattended-sweep'
created: '2026-08-06'
evidence: assertion
threshold: >-
  The census flags all three known-defective prefix guards. Fewer than three and
  the census does not answer this opportunity — it may still be built, but must
  be re-described as sizing a related population rather than as a response to
  this defect.
instrument: >-
  npx vitest run
  test/guards/provenance-census-scores-against-known-defects.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** A static analysis scored against three documented cases. No customer, no operator, no judgement call.

**What it does.** Run the provenance census over the suite. Assert its output contains all three prefix guards. This is a detector being graded on ground truth, which is the only honest way to introduce one.

**Why the expected outcome is failure, and why that is the point.** The solution this sits under predicts it will miss all three, because the three derived the prefix independently and share no symbol. Writing the test anyway is what converts that prediction from a caveat in prose into a claim that gets settled. A pass that skipped it would leave the census looking like a response to this opportunity when its own author already doubted that it is one.

**Why it is red today.** No census exists. Missing-file red, stated plainly — and this sweep could not read the repository to name a better path, for the permission reason recorded under "The agent's repo sight fails mid-pass, because nothing checked the product path before it was needed".

**What a green does NOT settle.** That the census's *other* findings are real defects rather than legitimate shared constants, or that anyone would act on the list. Both matter and neither is measured here.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/guards/provenance-census-scores-against-known-defects.test.ts` — No test files found, exiting with code 1
- 2026-08-17 **green** (exit 0) `npx vitest run test/guards/provenance-census-scores-against-known-defects.test.ts` — Duration  411ms (transform 17ms, setup 0ms, collect 182ms, tests 23ms, environment 0ms, prepare 24ms)
