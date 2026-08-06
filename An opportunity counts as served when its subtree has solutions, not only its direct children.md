---
type: Solution
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**The idea.** `underservedOpportunities` counts solutions in an opportunity's whole subtree rather than on its direct edges. An opportunity that has opportunity-children is a category, and a category whose children are well served is not a gap.

**Why.** The tree is explicitly multi-level — the ruleset says opportunities "nest into a multi-level sub-tree" and that "parent-child opportunity relationships represent subsets." Counting only direct solution edges assumes a flat layer that the same ruleset tells the agent not to build. The result is that re-parenting a solution onto the child it actually answers — which is good hygiene, and which the 2026-08-05 pass performed deliberately on three solutions — converts the parent into a permanent phantom gap. The tool punishes the restructuring the rules ask for.

**Sharper form.** Ideating under a parent whose children are served is not merely wasted; it is actively harmful, because the new solutions attach one level too high and address the category rather than the need. The next hygiene pass then has to re-parent them, which recreates the phantom. That is a loop that manufactures its own future work.

**Where it fails.** A parent opportunity can be a genuine gap — it can have children that are all served and still carry a distinct need of its own that nothing addresses. Subtree counting cannot see that case and would silently mark it served. This trades a loud false positive for a quiet false negative, which is the worse direction of the two if the parent needs are the important ones. A reader who wants the old view has no way to ask for it.

**Compared with its siblings.** "Every work bucket excludes nodes whose frontmatter says they are closed" fixes the shipped face and cannot touch this one, because a parent opportunity's status is legitimately `unvalidated`. "A disposition record every bucket consults" would fix this by letting a pass write down "served by children" once — more general, more expensive, and it requires someone to remember to write it, where this derives the answer from edges that already exist.

⚠️ Unvalidated. Agent-ideated.
