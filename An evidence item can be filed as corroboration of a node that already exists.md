---
type: Solution
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Corroboration can be recorded without asserting a new need]]

**The idea.** Give an evidence item a second disposition besides "became a node". A pass can file an item as corroborating an existing opportunity: the item leaves `unmappedEvidence`, its id is recorded on the target node, and the node's corroboration count goes up by one.

**Why this shape.** The parent's sharpest sentence is that a need observed 76 times and a need observed once look identical once each has a node. This is the only one of the three candidates that fixes that, because it is the only one that lands the observation *on the node it bears on*. The other two make the backlog smaller; this makes the tree richer. Frequency is the one thing the transcript corpus is uniquely good at measuring, and the tree currently throws all of it away.

**How it compares to its siblings.**
- "The queue groups identical friction shapes into one item" attacks supply — 76 items become four. Cheaper, mechanical, no judgement, and it still tells you nothing about which *need* the four bear on.
- "An unmapped item ages out of the queue into a digest" attacks the reporting only, and asserts nothing at all. It is the honest floor if judgement is too expensive to trust.

**Where it fails, stated so it can be judged.** Filing an item as corroboration is a judgement, and it is wrong in the direction that hides novelty: an item that looks like the four known frictions but carries a fifth is discharged and never read again. The parent says this explicitly and it is not solved by care. A mitigation worth designing in — corroboration is recorded reversibly, and the item stays readable under the node rather than being consumed — is the difference between this being safe and being a shredder.

It also does not decide *who* may file. An unattended pass filing its own observations as corroboration of its own prior observations is a loop grading itself, and that is a permission question, not a mechanism question.

**Cost.** A new disposition in the evidence store, a count on the node, and a tool verb. Moderate.

⚠️ Unvalidated. Agent-ideated during a pass that was itself facing the choice this node describes.
