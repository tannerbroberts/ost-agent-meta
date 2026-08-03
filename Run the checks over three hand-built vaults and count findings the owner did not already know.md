---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  Each of the 3 vaults yields at least 2 findings the owner calls new and worth
  fixing.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that the checks find something worth knowing in a tree someone built by hand and cares about. If the findings are all things the owner already knew or does not consider problems, the checker has nothing to sell however easy the sale would be.

**Risk category: desirability.**

**Design.** Find three people maintaining a discovery tree by hand and willing to let the checks run over it. For each finding, ask the owner: did you know, and does it matter? Count findings that are both new and considered worth fixing.

**Why it is small.** The checks already exist and run deterministically. The work is recruiting three vaults and one conversation each.

**What it will not cover.** Three vaults is a small sample and they will be trees whose owners were confident enough to share. A tree in worse shape might yield far more findings and belong to someone who would never volunteer it.

A human runs this and records the result.
