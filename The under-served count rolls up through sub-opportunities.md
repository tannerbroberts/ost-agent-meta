---
type: Solution
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Solutions beneath a category address the category's own need]]

**The idea.** `underservedOpportunities` stops counting a node's direct `#Solution` children and counts every solution in its subtree instead. A category holding 45 solutions two levels down reads as served, because it is.

**Why this shape.** It changes the arithmetic and nothing else. No new field, no new node property, no judgement about what a category is — the sweep already walks the tree to build the rollup, so the number is available at the point the check is made. The rollup printed at the head of every pass already computes exactly this figure; the queue and the rollup currently disagree about the same tree, and this makes them agree.

**How it compares to its siblings.**
- "A node with sub-opportunities is exempt from the under-served check" changes eligibility rather than arithmetic. It is cheaper and cruder: it never asks how much is beneath, only whether anything is. That makes it immune to the threshold argument below, and blind to a category with one sub-opportunity and nothing under it.
- "The queue reports the leaf it wants served, never the category above it" changes what is reported rather than how it is counted. It is the only one of the three that always hands the pass a node where a solution can legitimately hang.

**Where it fails, stated so it can be judged.** A rolled-up count asserts that solutions beneath a category address the category. That is usually true and not always: three solutions under one sub-opportunity would mark a category served while four sibling sub-opportunities beneath it have nothing. The count would be right and the tree would still be thin, and this fix would hide it. Whether the threshold should also scale with subtree width is the open question, and it is a human's.

**Cost.** One traversal already performed, one comparison changed, and fixtures pinning both directions.

⚠️ Unvalidated. Agent-ideated from a first-party observation made during the pass that wrote it.

## Definition of done

"A category whose subtree is full stops being reported as under-served"

```
npx vitest run test/ost/next-work-rollup-count.test.ts
```

The spec path is named, not linked — the test is wikilinked once already, by the assumption above it. Written without repo sight, so its first red is an absent file rather than a failing assertion; a builder should relocate the assertions into whichever existing spec covers the sweep.
