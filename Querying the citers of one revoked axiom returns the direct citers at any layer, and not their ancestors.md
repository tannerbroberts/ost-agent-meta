---
type: AssumptionTest
source: 'agent-ideated:2026-08-22-unattended-sweep'
created: '2026-08-22'
evidence: assertion
threshold: >-
  At least 4 assertions pass over a fixture holding 1 revoked axiom id: the
  query returns exactly the 2 nodes whose own `source` is that id; it returns
  them even though neither is an Opportunity; it does NOT return the 1 ancestor
  whose subtree contains a citer; and `claimsStoredEvidence` returns true for an
  `AXIOM:` id.
instrument: npx vitest run test/evidence/axiom-citation-index.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**Pre-committed threshold:** at least 4 assertions pass over a fixture holding 1 revoked axiom id — (1) the query returns exactly the 2 nodes whose own `source` is that id; (2) it returns them even though neither is an Opportunity; (3) it does **not** return the 1 ancestor whose subtree merely contains a citer; (4) `claimsStoredEvidence` returns true for an `AXIOM:` id. Fewer than 4 refutes the assumption as stated, and which assertion fails says which of the three gaps is the real one.

**What this measures, gap by gap.** Assertion (2) is the layer-keying gap: `evidenceExtents` returns Opportunity-keyed entries only. Assertion (3) is the subtree-versus-citation gap, and it is the one that would silently do damage if skipped — re-using extents directly would re-open every ancestor of a citer, which on this tree means re-opening whole buckets because one leaf cited a revoked axiom. Assertion (4) is the source-filter gap, deliberately included because this pass did not read `src/processes/tree.js` and will not assert what it does.

**Why it fails today, named from the code rather than assumed.** `evidenceExtents` filters its return to `n.layer === "Opportunity"`, so (2) cannot pass. Its extents are subtree unions, so (3) cannot pass against them. The `posting` map in `scanExtentOverlap` — the reverse index this test wants — is local to one loop iteration and never returned, so there is no exported query to call at all. All read first-party this pass.

**Honest limit on this instrument.** `test/evidence/axiom-citation-index.test.ts` does not exist, so this run files as `no-spec`: it fails for the reason any unwritten spec fails and does not on its own distinguish this question from another. The bound threshold above is what makes it a working permit rather than a placeholder — four assertions specific enough that a builder has a definition of done. An assertion-specific red is not reachable from this surface; the instrument grammar takes one whole spec file with no `-t` filter, and no tool here authors a spec.

**What a green here would NOT settle.** Feasibility only, and narrowly: that the index can answer the question. It says nothing about whether a human will ever author an axiom register, whether they would stand by an axiom when a derivation from it bites, or what "re-opened" should mean as a status transition — that last one is a product decision, since `ost_set_status` today has no re-open and `validated` is not an agent-settable value in either direction.
