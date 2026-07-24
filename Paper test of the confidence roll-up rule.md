---
type: AssumptionTest
status: unvalidated
source: 'agent:P4_assumptions'
created: '2026-07-24'
---
#AssumptionTest #unvalidated #feasibility

**Assumption under test (feasibility):** A stated propagation rule ranks branches by trustworthiness in a way informed humans recognise as fair.

**Proposed test:** Write the rule down on paper. Have three reviewers independently rank eight branches of the current tree from most to least trustworthy, without seeing the rule. Compare each ranking against the rule's output.

**Size:** an hour per reviewer; no code, uses the tree as it stands today.

**Pre-committed threshold:** at least 2 of 3 reviewers agree with the rule on both the top three and the bottom three branches. Disagreement in the middle is acceptable; disagreement at the extremes means the rule would mis-rank exactly the branches people act on.

**Decides:** whether propagation can be automated at all, or whether trustworthiness stays a human judgement the tree merely displays.

Proposed by the agent — to be run by a human with real reviewers. No results recorded here.
