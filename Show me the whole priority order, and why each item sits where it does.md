---
type: Opportunity
status: unvalidated
source: 'human:conversation'
created: '2026-07-25'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[A whole-tree ranked ledger that refuses to publish a row without its reason]]
[[Every row shows the named factors behind its rank, with no composite score]]

**The need (customer's voice):** "I want to be able to see a clearly prioritized list from top to bottom. Not just what is the highest leverage — but also, why." (Founder, verbatim, 2026-07-25.)

**Why it matters:** The parent opportunity is about having *any* ordering at all. This one is about the ordering being **complete and legible**: a single "build this next" answer doesn't let the operator plan past Monday, and a ranked list whose reasons are hidden inside the agent's head has to be taken on faith — which collides with every trust node in this tree ("Worry the agent is grading its own homework", "Would an operator accept an elimination they initially disagreed with once shown the evidence"). A ranking the operator can interrogate is one they can disagree with productively; an opaque one they can only obey or ignore.

**What the existing solutions don't cover:** [[A standing Next Build node the agent rewrites every pass]] names one item, not an ordering. [[Rank every node by how many blocked tests one build would unblock]] produces an ordering with one implicit reason (the count), but doesn't render the why beside each rank or handle items whose priority rests on something other than unblock leverage. [[Prerequisite edges between assumption tests]] gives structure the ordering could be derived from, but is not itself a legible list.

**Litmus test:** More than one way to address the "why" — per-item rationale prose the agent must write when it ranks, exposing the leverage computation itself (unblock counts, cost estimates), linking each rank to its evidence chain, contribution estimates laddering each item to the outcome metric, recorded pairwise comparisons. These trade off against each other. Passes.

**Placement:** Child of [[I have a tree full of unvalidated nodes and no idea which one to pick up]] — it sharpens what "picking one up" requires rather than naming a new top-level pain.

Evidence: founder statement in conversation, 2026-07-25.

## History
- 2026-07-25 evidence: (none) → assertion — founder-stated need, verbatim quote preserved; no external party involved; floor rung per the ladder's rule.
