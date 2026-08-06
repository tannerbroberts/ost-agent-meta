---
type: Assumption
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Count how many underserved opportunities have a solution somewhere beneath them]]

Feasibility, and it is the load-bearing one: subtree counting is worth building only if the phantom gaps are most of the list rather than a handful.

Stated so it can be false: if the 30 opportunities reported underserved on 2026-08-06 are mostly genuine leaves with no solutions anywhere beneath them, then this change removes a few noisy entries and leaves the real backlog untouched, and the cheaper reading is that the tree simply needs more ideation.

The count that would settle it is mechanical — for each opportunity in `underservedOpportunities`, does its subtree contain a Solution? Eyeballing the 25 shown on 2026-08-06 suggests roughly half are bucket categories carrying large subtrees, but that is an eyeball over a truncated list and is exactly the kind of estimate this assumption exists to replace.

The failure mode on the other side is quieter and is not measured by this test: a parent opportunity that carries a real need of its own, distinct from all of its children's, would be marked served by subtree counting and would stop being offered. Whether any such node exists in this tree is a separate question.
