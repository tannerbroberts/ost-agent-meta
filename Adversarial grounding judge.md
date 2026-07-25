---
type: Solution
status: unvalidated
evidence: assertion
source: 'agent:P3_ideate'
created: '2026-07-24'
---
#Solution #unvalidated #evidence/assertion
[[Critic pass rated for actionability]]

A separate reviewer pass whose only job is to attack the tree: for each node, state the strongest case that it is wrong, name what evidence would settle it, and annotate the node with what is missing. It never writes new opportunities and never removes anything — it lowers unearned confidence.

**How it differs from its siblings:** the other two make existing provenance legible; this one goes looking for provenance that *should* exist and doesn't. It is the only sibling that can catch a well-labelled, well-propagated, entirely wrong branch.

**Trade-off:** costs a full pass of compute, and an over-eager critic floods the tree with objections nobody reads.

**Riskiest assumptions to test:** that an independent critic finds objections a human agrees are worth acting on (desirability); that its output stays small enough to read (usability).

Status: agent-originated candidate. Unvalidated.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule

## Issues
- 2026-07-25 Cross-branch redundancy (2026-07-24 review): same underlying bet as 'Independent LLM judge scores faithfulness to evidence' and 'Independent judge separate from the proposer'. One build satisfies all three; consolidation candidate.
