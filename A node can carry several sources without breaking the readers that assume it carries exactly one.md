---
type: Assumption
source: 'agent-ideation:2026-08-22-unattended-sweep'
created: '2026-08-22'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

**The belief, stated so it could be false (feasibility).** `source` is a string today, and this candidate makes it a list. The assumption is that the blast radius of that change is bounded — that the readers consuming `source` either already tolerate a list or can be made to without cascading.

It could easily be false. `source` is not a decorative field in this product: the believability ladder caps a node's rung by *what its source has earned as an actor*, the trust ledger keys standing off it, `quotableSource` flattens it into hygiene findings, the rollup counts distinct sources per bucket, and the dangling-citation hygiene rule parses it. A node with three sources on three different rungs raises a question the ladder has no answer for today — is the node's ceiling the highest of them, the lowest, or something else — and that is a semantic decision, not a serialization detail. If the honest answer turns out to be "the weakest, so adding a source can *demote* a node", the candidate acquires a consequence nobody ideating it intended.

What is being tested here is the narrow, mechanical half: do the readers survive. The semantic half — what a multi-source node's rung *should* be — is a design question a test cannot settle, and it is named here so nobody mistakes a green run for having answered it.
