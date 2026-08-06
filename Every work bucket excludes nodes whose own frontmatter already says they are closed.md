---
type: Solution
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**The idea.** `computeNextWork` filters every bucket by the node's own `status` before listing it. A solution with `status: shipped` or `status: deferred` is not missing an instrument — it is finished or abandoned — and does not appear in `solutionsMissingInstruments`. The same filter applies wherever a bucket selects nodes.

**Why this one first.** It is the cheapest of the three and it needs no new state at all. The information is already on the file: five of the listed solutions say `status: shipped` in their own frontmatter, written there by an earlier pass that had read the code and checked. The sweep simply does not consult it. Nothing has to be invented, remembered, or maintained — a predicate has to read a field that is already populated.

**What it fixes and what it does not.** It clears the shipped face outright. It does nothing for the parent-opportunity face, because a parent opportunity is legitimately `unvalidated` — its status is not what makes it a non-gap. And it does nothing for the evidence face, which has no node to carry a status.

**Where it fails.** It trusts `status: shipped` without checking the repository, and that trust is exactly what an agent grading its own repairs should not be given for free. A pass that wants an item off the list can now set `shipped` instead of writing an instrument — a cheaper escape than the one this replaces, and pointed the same direction. The mitigation is that `ost_set_status` records the transition in History with a note, so the escape is at least legible; the sibling test "Audit every shipped solution against the repository before trusting the exclusion" already exists and is the check that would catch it.

**Compared with its siblings.** "Count an opportunity's whole subtree" fixes a different face and neither subsumes this. "A disposition record every bucket consults" is the general form of this one — it would cover all three faces, and costs a new store and a new write path. This is the special case that needs neither, and shipping it does not foreclose the general form.

⚠️ Unvalidated. Agent-ideated from the agent's own observation of the surface it is graded through.
