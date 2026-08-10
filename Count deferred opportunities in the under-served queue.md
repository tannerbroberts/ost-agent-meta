---
type: AssumptionTest
source: 'agent-run:autonomous-loop-2026-08-09'
created: '2026-08-10'
evidence: assertion
threshold: >-
  Zero opportunities carrying status: deferred appear in
  underservedOpportunities, over a fixture vault that contains at least one
  deferred opportunity with fewer than minSolutionsPerOpportunity direct
  solution children.
instrument: npx vitest run test/ost/underserved-excludes-deferred.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.**

**The bar, fixed before anything is built.** Build `computeNextWork` over a fixture vault holding at least one Opportunity with `status: deferred` and fewer direct Solution children than `minSolutionsPerOpportunity`. `underservedOpportunities` must contain **zero** entries carrying that status. A single deferred entry fails the test.

**Why it is red today, and by which of the two reds.** This is the stronger kind: the behaviour was verified absent by *running the tool and reading what it returned*, not by pointing at a file that does not exist. On 2026-08-09 the live `ost_next_work` returned `underservedOpportunities` containing exactly one entry — "Want proof no hijackable capability even exists" — reported as `solutions: 2, needed: 3`, while the **same response** listed that node under `retiredFromDuplicateScan` with the reason "status: deferred — retired, withheld from the duplicate scan". A spec asserting the exclusion therefore fails against today's code on the assertion, not on the import.

**The second assertion, which is what makes this a test of the design rather than of one predicate.** Pin the consistency directly: for any node the sweep withholds from one analysis on the grounds of its status, no other analysis in the same response may demand work for it. That is the invariant the observed output actually violates, and it fails today for the same node.

**What this does NOT settle.** Four things, and the first is the important one.

1. **Nothing about whether the exclusion should exist.** A green spec proves the filter can be built and was absent. The parent solution's own stated failure mode is that `deferred` also marks parked-but-unsettled work, so hiding it may cost the operator the one surface that would have resurfaced it. That is a desirability question and no exit code touches it.
2. Nothing about the `shipped` half of the queue defect — the five shipped solutions in `solutionsMissingInstruments` are a different builder and would still be offered.
3. Nothing about whether a human wants "Want proof no hijackable capability even exists" to stay retired. Its deferral was a human-authorized merge; this test assumes that decision stands and does not re-open it.
4. Nothing about the other 61 solutions in the instrument queue.

**One caveat on the instrument itself, recorded rather than hidden.** This pass could not read the product repository — `product.repos` is unconfigured and product-directory reads are denied on this surface — so it could not confirm that `test/ost/underserved-excludes-deferred.test.ts` does not already exist, nor name the module that has to change. If a spec of that name already exists and passes, this instrument is green on arrival and measures nothing, and that should be checked before anyone builds against it. The path follows the convention its sibling uses (`test/ost/instrument-queue-excludes-shipped.test.ts`).

⚠️ Unvalidated. Proposed, not run — no result is recorded and none may be recorded from an unattended pass.
