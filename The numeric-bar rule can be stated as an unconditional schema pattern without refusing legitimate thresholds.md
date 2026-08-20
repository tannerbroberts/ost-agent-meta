---
type: Assumption
source: 'agent-ideation:2026-08-20-unattended-sweep'
created: '2026-08-20'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Run a digit-required pattern over a fixture of this vault's existing thresholds and count the legitimate bars it refuses]]

**Kind: feasibility.** The belief is that "a threshold must carry a digit" can hold for every AssumptionTest, not only for those whose instrument is no-spec, so the rule can live on the `threshold` property of the input schema and be reported by `validateToolInput` per field. It would be false if the tree's existing tests include thresholds that are legitimately non-numeric — a bar stated as a refusal ("the guard refuses the write"), an ordering, or a presence check — because an unconditional pattern would start refusing those, and the conditional half would have to stay in the tool body, which is the hand-written path the solution set out to remove.

Stated so it can fail: applied to every AssumptionTest threshold already in this vault, a digit-required pattern refuses none of the ones a human reads as a fixed bar.
