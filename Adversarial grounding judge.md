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

## Definition of done

[[Critic pass rated for actionability]]

`npx vitest run test/eval/adversarial-critic-invariants.test.ts`

The spec asserts the two invariants that make this a critic rather than another author: a critic pass creates no nodes and removes nothing, and every objection it emits names the evidence that would settle it. Both are stated in the node as the defining constraints — it "never writes new opportunities and never removes anything — it lowers unearned confidence" — so they are the right things to make falsifiable. Red today because no critic pass exists and nothing enforces the boundary.

**What a green here does not settle.** Both of the node's own riskiest assumptions, and it names them: that an independent critic finds objections a human agrees are worth acting on (desirability), and that its output stays small enough to read (usability). An over-eager critic that floods the tree with well-formed, correctly-cited objections nobody reads would pass this spec perfectly. Actionability is the humans-required test.

**Unresolved, and not this pass's call.** The 2026-07-25 issue above flags this as one of three nodes making the same bet, with "one build satisfies all three". This sweep did not merge them: an adversarial critic, a faithfulness scorer, and an independent judge separate from the proposer are plausibly one mechanism and plausibly three, and the difference turns on whether attacking a claim and scoring its fidelity to evidence are the same act. What would settle it: write the one build's interface and see whether all three nodes' described outputs fall out of it. If they do, merge into this one and carry the others' prose across.
