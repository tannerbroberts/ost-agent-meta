---
type: Solution
status: unvalidated
source: 'agent:P3_ideate'
created: '2026-07-24'
---
#Solution #unvalidated

A separate reviewer pass whose only job is to attack the tree: for each node, state the strongest case that it is wrong, name what evidence would settle it, and annotate the node with what is missing. It never writes new opportunities and never removes anything — it lowers unearned confidence.

**How it differs from its siblings:** the other two make existing provenance legible; this one goes looking for provenance that *should* exist and doesn't. It is the only sibling that can catch a well-labelled, well-propagated, entirely wrong branch.

**Trade-off:** costs a full pass of compute, and an over-eager critic floods the tree with objections nobody reads.

**Riskiest assumptions to test:** that an independent critic finds objections a human agrees are worth acting on (desirability); that its output stays small enough to read (usability).

Status: agent-originated candidate. Unvalidated.
