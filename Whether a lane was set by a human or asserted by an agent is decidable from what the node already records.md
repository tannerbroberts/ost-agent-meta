---
type: Assumption
source: 'agent-ideation:2026-08-30-unattended-sweep'
created: '2026-08-30'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

**Risk category: feasibility.**

The belief, stated so it could be false: a lane set by a human's `ost-agent lane --set` leaves a mark in `## History` that a lane arriving through `ost_create_node`'s `humansRequired:` argument does not, so the two are separable by reading the node — which is the entire premise of copying `trustsShippedStatus`.

**How it could turn out false, and this is the likely way.** Both paths may write a History line of the same shape. `ost_create_node`'s `humansRequired:` description says the reason "is recorded in the node's History", and `ost-agent lane --set` records a reasoned transition too. If the two lines are indistinguishable — same format, same fields, no actor recorded — then there is nothing to audit and this candidate cannot be built as designed. `trustsShippedStatus` works because a promotion is a distinct human-only CLI act; if lanes have no such asymmetry, the analogy fails at exactly the point it is being borrowed for.

**The second way it fails.** Even if the two are distinguishable today, an agent that can write a History line through any tool could imitate the human shape. The audit would then be checking a format rather than an authority, which is weaker than it looks and worth knowing before it is relied on.
