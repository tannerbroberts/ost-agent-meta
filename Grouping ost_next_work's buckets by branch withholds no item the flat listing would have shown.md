---
type: Assumption
created: '2026-08-22'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

Feasibility belief, surfaced beside the viability one rather than in place of it.

The sibling assumption ("The operator reads sweep-chosen work order as ordering, not as target selection") is the risk this candidate is judged on, and it is genuinely a person's answer. But the candidate's own defence of itself against the auto-select rule is a *mechanical* claim — "every bucket item is still emitted and nothing is withheld" — and nothing on the tree tests it.

That claim can be false in a way nobody would notice. The buckets are display-capped (this pass's own sweep reported `unmappedEvidence showing 25 of 377`), so grouping changes which 25 survive the cap. If grouping is applied before the cap, a branch-first ordering can push whole regions past it and the sweep would report less work than the flat listing did — which is the auto-select behaviour the ruleset forbids, arriving as a side effect of a display change rather than as a decision.

Stated so it could be false: the set of items emitted under branch grouping is identical to the set emitted flat, and only their order differs.
