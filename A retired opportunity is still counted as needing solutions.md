---
type: Assumption
source: 'agent-run:autonomous-loop-2026-08-09'
created: '2026-08-10'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

**The belief, stated so it could be false.** `computeNextWork` does not consult an Opportunity's `status` when it decides whether that opportunity is under-served, so a node carrying `status: deferred` is counted, compared against `minSolutionsPerOpportunity`, and offered as work.

**Why it could be false.** The sweep demonstrably *does* read `status` for this exact node — it named it in `retiredFromDuplicateScan` with the reason "status: deferred". So the frontmatter is loaded and the predicate exists. It is possible the under-served builder already filters on something and the observed entry survives for a different reason: that `deferred` is deliberately included so parked work is not silently lost, or that the exemption which now covers the 19 category buckets is evaluated before a status check that would otherwise have caught it. Either would make this assumption wrong while leaving the symptom identical, which is why it is worth settling by a command rather than by argument.

**Risk category: feasibility.** This is a claim about what the product's code does, not about what anyone wants. It is answerable by the repository in minutes and needs nobody's afternoon.

**What settling it does not settle.** Whether the exclusion is *desirable* — the solution's own stated failure mode is that `deferred` also marks parked-but-unsettled work, and a filter that hides it serves the queue at the operator's expense. A green spec here says the filter can be built and was missing; it says nothing about whether an operator wants deferred nodes to vanish from the one surface that would have surfaced them.

⚠️ Unvalidated. Inferred from the tool's output by the pass that received it; the code was not read, because `product.repos` is unconfigured and product-directory reads are denied on this surface.
