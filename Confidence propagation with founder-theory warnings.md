---
type: Solution
status: unvalidated
source: 'agent:P3_ideate'
created: '2026-07-24'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A branch reading as only as strong as its weakest input changes what people act on]]

Roll evidence strength up the tree: a branch is only as believable as its weakest load-bearing input, and the tree surfaces that — "this entire branch rests on founder theory", "this opportunity has no non-founder source" — wherever the branch is read or acted on.

**How it differs from its siblings:** structural rather than per-node. It answers "can I act on this part of the map?" instead of "where did this sentence come from", and it makes the absence of evidence visible, which labelling alone does not.

**Trade-off:** any roll-up rule is an opinion about how confidence combines, and a wrong rule quietly mis-ranks whole branches.

**Riskiest assumptions to test:** that a propagation rule can be stated that people accept as fair (feasibility); that seeing a weak-branch warning actually redirects effort toward grounding it (desirability).

Status: agent-originated candidate. Unvalidated.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked "Paper test of the confidence roll-up rule" — moved under "A branch reading as only as strong as its weakest input changes what people act on" — the belief this test measures now has a node of its own

## Definition of done

"Paper test of the confidence roll-up rule"

`npx vitest run test/ost/branch-provenance-warning.test.ts`

**Half of this node already ships, and the instrument is aimed at the half that does not.** The weakest-rung roll-up is live — the rollup reports `rests on assertion` per bucket with a source count, which is "a branch is only as believable as its weakest load-bearing input, surfaced wherever the branch is read". What is not built is the second warning the node quotes: *"this opportunity has no non-founder source"*. Nothing today distinguishes fourteen internal sources from one outside voice, so a bucket resting on fourteen founder notes and agent-generated channels reports identically to one with an external party in it. The spec asserts a branch whose sources are all internal is flagged as having no external source, and it is red against today's output rather than against a missing file.

**What a green here does not settle.** Both riskiest assumptions the node names. That a propagation rule can be stated which people accept as fair is a judgement about the rule, not about the code — any roll-up is an opinion about how confidence combines, and a wrong one quietly mis-ranks whole branches while passing every test. And that seeing a weak-branch warning actually redirects effort toward grounding it is desirability: this tree has reported `rests on assertion` on all thirty-four buckets for some time, and the rung has not moved, which is weak early evidence against exactly that assumption.
