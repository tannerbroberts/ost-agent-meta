---
type: Assumption
source: 'agent-ideation:2026-08-06-unattended-sweep'
created: '2026-08-06'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

**The belief, stated so it could be false.** Unblocking leverage is unevenly distributed across a real tree, so ordering by it separates the candidates rather than declaring them all equal.

**Why this belongs beneath this solution and is not covered by its existing test.** The solution's own body names this as the prerequisite check — *"If most tests turn out to be independent, leverage is near-uniform and the ranking says nothing... The assumption test under this node checks the ratio before anyone builds the graph machinery."* But the test that actually hangs beneath it, "Hand-compute unblock counts and see if the operator's pick changes", measures something else and later: whether a *person's choice* moves once they are shown the numbers. That is a desirability question and it correctly needs a person. The distribution question is prior to it, is a property of the tree, and needs nobody — and if leverage is flat, the operator study is a study of a ranking that cannot rank, run at the cost of somebody's afternoon.

**What class this is.** Feasibility. The evidence sits in this vault already: 1,007 nodes, 297 assumption tests, 291 solutions.

**How it could come out false.** The only supporting datum is a single 4:1 ratio observed once in the sibling `tetrix-ost` tree, and the solution says so. A tree whose tests are mostly independent — which is the shape you would expect if each solution got its own bespoke test, and this tree's 297 tests under 291 solutions is exactly that shape — would produce a flat distribution and refute the ranking's whole premise.
