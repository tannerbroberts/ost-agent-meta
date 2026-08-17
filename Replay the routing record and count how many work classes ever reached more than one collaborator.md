---
type: AssumptionTest
source: 'agent-ideated:2026-08-03-unattended-sweep-builder-capability'
created: '2026-08-03'
evidence: assertion
threshold: >-
  At least 40% of distinct work classes in the recorded history must have been
  routed to more than one collaborator. Below 25% kills the candidate.
instrument: npx vitest run test/product/routing-record-capability.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**The assumption under test (viability):** that routing outcomes carry enough variation to be an estimate rather than a record of habit. An outcome ledger only distinguishes capability from assignment history if the same class of work has been given to more than one party. If every class has exactly one owner, the ledger says "the person who does this does this" and dresses a tautology as a profile.

**The test:** replay the recorded work history in this vault and the OST-Agent repo. Classify each assignment by work class — build, review, discovery pass, release, decision — and count what fraction of classes were ever routed to more than one collaborator. Entirely retrospective, against committed state, no operator and no build.

**Pre-committed before running, so this can come out a failure:** at least 40% of classes must show more than one collaborator. Between 25% and 39% means the estimate ships only over the classes that qualify, with the single-owner classes shown as unestimated rather than as confident. Below 25% kills the candidate — at that concentration the profile cannot correct itself, which is the self-confirming failure the solution names as its chief risk, confirmed before anything is built.

**What it deliberately does not cover, and a human should weigh this separately:** the candidate's second risk is not measurable this way at all. An outcome ledger over named people is a performance record, and whether one may exist here — who may read it, whether a collaborator may see their own, whether it may inform anything but routing — is a governance question this vault has never ruled on. A green result on this test says the mechanism *could* work; it says nothing about whether it *should*, and the two must not be conflated when this candidate is compared against its siblings.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/product/routing-record-capability.test.ts — Replays the routing record and counts work classes with more than one collaborator, which is the comparison any capability estimate needs; fails today because nothing derives capability from what was asked and what came back.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/product/routing-record-capability.test.ts` — No test files found, exiting with code 1
- 2026-08-17 **green** (exit 0) `npx vitest run test/product/routing-record-capability.test.ts` — Duration  1.32s (transform 39ms, setup 0ms, collect 61ms, tests 1.07s, environment 0ms, prepare 27ms)
