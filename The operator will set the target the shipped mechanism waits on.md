---
type: Assumption
source: 'observation:2026-08-11 ost_next_work returned no scope field'
created: '2026-08-11'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

**Kind: desirability.** The shipped mechanism is inert until a human writes one line — `discovery.target` in `ost.config.yaml` — and no tool can write it for them, by design. The belief, stated so it can be false: an operator who asked for branch-at-a-time discovery on 2026-08-11, and had the mechanism shipped the same day, will perform the one-line act that turns it on.

What makes this worth testing rather than assuming: this tree's own record is full of one-line human actions that stayed unperformed for days while every pass re-derived their absence — `product.repos` took seven passes and six recorded sightings to get set; the four pricing tests' lane labels were specced as exact CLI commands on 2026-08-05 and remain unrun. The operator's hours are the scarcest input this product has ("I need the tree's output to be actionable by compute alone, because my hours don't exist"), and this mechanism's first act is to spend one.

Observed at ideation time: the sweep of 2026-08-11 (the firing after the ship) returned no `scope` field — no target set yet.
