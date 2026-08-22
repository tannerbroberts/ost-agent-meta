---
type: Assumption
source: 'agent-ideated:2026-08-22-unattended-sweep'
created: '2026-08-22'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Querying the citers of one revoked axiom returns the direct citers at any layer, and not their ancestors]]

**Feasibility assumption, stated so it can be false.** This solution's prose commits to a mechanism nothing else on the node accounts for: "revising or revoking an axiom is a recorded act that **re-opens every derivation citing it**." That needs an answer to "which nodes cite X" — a reverse index over citations. The belief recorded here is that the index already exists in this repository in all but its keying, so revocation is a small change rather than new machinery. It may be false, and the reasons it might be are named below.

**What the code shows, read first-party this pass (`src/ost/extent.ts`, read in full).**

- `evidenceExtents(nodes)` does exactly the forward half: a memoised post-order walk that accumulates, for a node, the set of stored-evidence ids cited by it or anything beneath it. Cycle-safe, linear, already shipped.
- `scanExtentOverlap` then builds `posting: Map<recordId, position[]>` — **a literal reverse index from a cited record to the nodes citing it.** It is constructed and discarded once per parent, because its only consumer is the sibling-overlap comparison.

So the claim's hardest-sounding part is the part that is done.

**Three gaps stand between that and revocation, and each is why this could still be false.**

1. **Layer keying.** `evidenceExtents` returns entries only for `n.layer === "Opportunity"`. A derivation is not necessarily an Opportunity, so the map as returned cannot answer the question for the nodes revocation cares about. The walk is general; the output is not.
2. **Subtree, not citation.** An extent is what a node *or anything beneath it* cites. "Derivations citing axiom A" is a strictly narrower relation — a node whose child cites A is in the extent and is not a citer. Re-using extents directly would over-return, re-opening derivations that never cited the revoked axiom.
3. **The source filter.** Entry into an extent is gated on `claimsStoredEvidence(node.source)`. Whether an `AXIOM:<id>` source passes that predicate is unknown — this pass did not read `src/processes/tree.js`, and says so rather than guessing. If it does not, nothing about axioms is indexed at all and gap 3 is the whole problem.

**Why this belongs beside the sibling rather than inside it.** The solution's only other assumption is "An up-front authoring session produces axioms the founder still endorses when they matter" — a desirability question about a person's time and conviction, correctly a person's to answer. This one decides whether the revocation half is an afternoon or a subsystem, and a spec settles it. A builder handed only the desirability question would scope this solution wrong.

_Method: first-party `ost_read_repo` of `src/ost/extent.ts`, read in full (`truncated: false`). `src/processes/tree.js` deliberately not read, so gap 3 is stated as unknown rather than answered. Nothing executed. Grounds feasibility only. Rung stays at the `assertion` floor._
