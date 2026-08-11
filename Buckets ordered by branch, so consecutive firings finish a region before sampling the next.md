---
type: Solution
source: 'CONVO:2026-08-11 operator session'
created: '2026-08-11'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**Mechanism:** `ost_next_work` emits every bucket grouped by branch instead of tree-walk (effectively alphabetical) order — all of one region's outstanding items surface together, and the next region is not sampled until the first reports clean. The observed failure this answers is the display-capped alphabetical slice: fourteen consecutive passes re-deriving the same global queue and finishing no region of it.

**Contrast with the sibling "A discovery firing scoped to one human-chosen target branch, worked to done before the sweep widens":** that solution produces dwell only after a human writes `discovery.target`; this one produces dwell with no human act, on the unscoped sweep that actually runs when no target is set — which, as of the firing that ideated this, is every firing, because the shipped target mechanism is still unset.

**The viability risk is the ruleset itself, named rather than papered over:** `ruleset.ts` MUST NOT auto-select a target opportunity. Ordering all work is not declaring a target — every bucket item is still emitted and nothing is withheld — but the region worked *first* becomes an agent choice, and whether the operator reads that as ordering or as selection is exactly the question the assumption beneath this must settle before anyone builds it.
