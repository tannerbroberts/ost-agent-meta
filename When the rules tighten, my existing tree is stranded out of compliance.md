---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-24-friction-a-new-node-level-requirement-is-unfixable-for-ex.md'
created: '2026-07-25'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[An upgrade changed what counts as done, so finished work silently reopened]]
[[New rules apply forward only, and existing nodes are marked as predating them]]

Each new node-level requirement (a required field, a new invariant) instantly flags every node created before it, and the append-only design offers no compliant path to fix them: each frontmatter field needs its own purpose-built setter tool before an existing tree can comply. Every future required field hits the same wall.

Grounding: adding the evidence-class invariant flagged all 57 then-existing nodes with no generic remediation path (agent-filed friction, kind: missing-affordance, 2026-07-24). The 0.4.0 upgrade separately reopened 18 mapped evidence items when done-ness accounting changed (see [[The pass never says it is done, so I can't tell when to stop paying for compute]]).

Litmus: versioned invariants that only bind nodes created after them; audited migration passes; generic history-preserving setters; grandfather annotations — multiple distinct ways. Distilled by the mapping agent from agent-self-reported observation; unvalidated.
