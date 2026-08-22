---
type: Assumption
source: 'agent-ideated:2026-08-22-unattended-sweep'
created: '2026-08-22'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[A proof rung resolves through its cited axioms instead of returning a constant rank]]

**Feasibility assumption, stated so it can be false.** This solution proposes conclusions carrying evidence `proved-given-axioms`, "believable exactly as far as the axioms". That is not a position on the ladder — it is a *function* of what the node cites. The belief this node records is that such a thing can be added to the existing ladder without breaking the consumers that read a rung as a scalar. It may not be, and the code gives a reason to doubt it.

**What the code shows, read first-party this pass (`src/knowledge/believability.ts`, read in full).**

- `BELIEVABILITY_LADDER` is five entries, `as const`, and `RungId` is derived from it. Adding a sixth id is cheap at the type level.
- `rungRank(id)` returns **one integer per id**, from a `Map` built off the array index. A `proved-given-axioms` node has no fixed integer — its weight moves with its citations — so there is no honest value for this function to return for it.
- `weakestRung` folds a list of rung ids to the worst one, coercing anything unrecognised to the floor: `const id = isRung(r) ? r : FLOOR_RUNG`. So the "only as believable as its weakest input" rule *already exists* and is exactly the rule a proof lane needs — but it is called on flat lists of node rungs, never across a citation edge. Nothing walks from a conclusion to what it was derived from.
- `classifyProvenance` is fail-closed: an unrecognised prefix returns `FLOOR_RUNG`, and its docstring argues for that ("an unearned rung is worse than an obviously unproven one"). So an `AXIOM:`-sourced node lands on the floor today, silently.
- `believabilityRollup` reports `weakest` over the node set. A rung with no scalar rank has no defined contribution to that line.

**Why this is worth writing down separately from the sibling beside it.** The solution's only other assumption is "An axiom's owner will stand by it when a derivation from it bites" — a desirability question about a person, correctly answered by a person. This one is about whether the mechanism can hold the shape at all, and it is settleable by a spec against code that exists. A builder handed only the desirability question would start building and meet this on the first afternoon.

**What would make it false.** If a proof rung has to be given a fixed rank to satisfy `rungRank`, then it is not "as believable as its axioms" — it is a constant, and the solution's central claim is not implementable in this ladder without changing every consumer's contract from scalar to resolver. That is a larger change than the node's prose implies, and it is the thing the test beneath this should find out.

_Method: first-party `ost_read_repo` of `src/knowledge/believability.ts`, read in full (`truncated: false`). Nothing executed. Grounds feasibility only — it says nothing about whether anyone wants a proof lane. Rung stays at the `assertion` floor._
