---
type: Assumption
source: 'agent-ideation:2026-08-20-unattended-sweep'
created: '2026-08-20'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

**Kind: viability — a permission, not a capability.** The mechanism is a few lines of `gh pr merge`; the belief that has to hold is that the operator is willing to have trunk change on the strength of a green suite and a transitioned instrument, with no human reading the diff. Everything recorded on this tree about the build loop's permits has been built in the opposite direction — `gate` is human-only, `verify` runs outside the model, the ship step refuses a dirty tree — and "Ask the founder whether a machine-cleared permit may start a build with nobody watching" is still an outstanding ask with no answer on record. Merging is one step past starting.

**Stated so it could be false:** asked plainly, with the third firing's improvised merge on PR #181 in front of them, the operator says yes to unattended merge under named conditions (green CI, instrument transitioned, no `## Uncovered` gap, squash only).

**What would change if it were false.** The solution is dead as a candidate and the window it would have closed stays open; the two siblings beneath the same opportunity carry the need instead.

**Not answerable from the repository.** No spec can observe a permission that has not been given; this is the operator's sentence or nothing.
