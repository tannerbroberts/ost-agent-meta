---
type: AssumptionTest
created: '2026-08-22'
evidence: assertion
threshold: >-
  zero items present in the flat listing are absent from the branch-grouped
  listing, and reported totals match between the two
instrument: npx vitest run test/mcp/branch-grouped-buckets.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** Nobody is the measurement here — the question is whether two orderings of one list hold the same members, which is a set comparison against a fixture tree.

**Design.** Build a tree with items spread across at least three branches and more outstanding items than the display cap. Compute the sweep flat, compute it branch-grouped, and compare: the multisets must be equal, and in the grouped listing each branch's items must be contiguous. Then assert the cap is applied to the *reported* slice only, so the grouped listing's `total` counts still name the full set.

**Pre-committed threshold:** zero items present in the flat listing are absent from the branch-grouped listing, every branch's items are contiguous in the grouped order, and the reported totals match between the two.

**What this does not settle.** It is a feasibility measurement and nothing else. A green here says the grouping withholds nothing; it says nothing about whether the operator reads a chosen order as target selection, which is the sibling assumption and stays a person's answer. Nor does it say dwell actually improves — that a firing finishes a region is a separate observation over consecutive firings.
