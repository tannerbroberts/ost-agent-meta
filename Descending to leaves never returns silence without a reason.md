---
type: AssumptionTest
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
threshold: >-
  A fixture category considered short whose every leaf is at or above the
  threshold produces an explicit diagnostic entry naming the empty descent, not
  an absent one.
instrument: npx vitest run test/ost/next-work-leaf-redirect.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**What it measures.** The failure mode that would collapse this candidate into its cheaper sibling. If an empty descent is indistinguishable from a healthy branch, redirection buys nothing over exemption and costs a traversal.

The bar is deliberately about the *diagnostic*, not about the count. It is fine for the descent to find nothing; it is not fine for the pass to be unable to tell that from a served branch.

**Why it is red today.** There is no descent, so there is no empty-descent case and nothing to report about it.

**Honest limit on the instrument.** No repo sight was available to this pass, so the path is invented and its first red is an absent file. A builder should relocate the assertions into the existing spec for the sweep.

**What a green here does not settle.** Whether the diagnostic is one a human would act on, and whether the ordering rule for a leaf reachable from several branches is right — both are design questions this file does not touch.

## Instrument Log
- 2026-08-07 **red** (exit 1) `npx vitest run test/ost/next-work-leaf-redirect.test.ts` — No test files found, exiting with code 1
