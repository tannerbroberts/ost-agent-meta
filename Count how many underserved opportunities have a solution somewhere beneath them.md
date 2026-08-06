---
type: AssumptionTest
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
threshold: >-
  At least half of the opportunities reported underserved must have a Solution
  somewhere in their subtree. Below half, the phantom-gap theory is refuted and
  this candidate should lose to plain ideation.
instrument: npx vitest run test/ost/underserved-subtree-count.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** Walk every opportunity `computeNextWork` reports as underserved, count Solutions in its full subtree rather than on its direct edges, and assert the bucket lists only those whose subtree count is under the minimum.

**Why it is red today.** The bar is fixed in advance and stated above. The assertion describes behaviour observed absent: on 2026-08-06 "The same refusal is rediscovered every session, because nothing carries the lesson forward" was reported with `solutions: 0`, while its own body records that three candidate solutions were re-parented onto its child "A correction lives only as long as the session it was given in" and says outright that it "reads as underserved in `ost_next_work` for that reason — it is a parent opportunity now, not a gap." Counting is by direct edge today; a spec asserting subtree counting fails on the mechanism, not on the missing file.

**What a green run does not settle.** It measures how many phantom gaps exist and confirms the new predicate counts subtrees. It cannot detect the failure this change introduces — a parent opportunity carrying a real need of its own, distinct from every child's, which subtree counting would mark served and stop offering. Nothing mechanical can distinguish that from a category, because the difference is what the need means. It is also silent on whether an operator would rather see the noisy list than risk the quiet omission.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/ost/underserved-subtree-count.test.ts` — No test files found, exiting with code 1
