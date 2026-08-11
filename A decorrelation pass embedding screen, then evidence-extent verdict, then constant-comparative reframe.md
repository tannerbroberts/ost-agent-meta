---
type: Solution
status: shipped
source: 'CONVO:2026-08-11 literature research pass'
created: '2026-08-11'
evidence: expert
---
#Solution #unvalidated #evidence/expert
[[Extent flags mostly point at real duplicates, not at distinct needs sharing a source]]

Three stages, each borrowed from an established method, run per sibling set (siblings are the comparison set prioritization actually uses, so overlap between distant cousins is lower-stakes):

**1. Candidate generation — embedding-similarity screen (SemDeDup-style, arXiv 2303.09540).** Embed node statements, flag sibling pairs above a cosine threshold. Cheap and unattended; replaces/extends today's title-Jaccard in `src/ost/dedupe.ts`. Known failure mode — it flags shared vocabulary, not shared need — is harmless because it only nominates pairs, never adjudicates.

**2. Objective verdict — evidence-extent analysis (Formal Concept Analysis, Ganter & Wille).** The vault already stores exactly the input FCA needs: which evidence records support which node. Same extent ⇒ same concept, merge via `ost_merge_nodes` (already granted to the pass). Strict-subset extent ⇒ parent/child mis-hung as siblings, re-link. Substantially overlapping but crossing extents ⇒ genuinely entangled, go to stage 3. This converts Torres's own semantics ("a child is a subset of a parent"; siblings are "distinct — you can address one without addressing another") into auditable set arithmetic.

**3. Resolution — constant-comparative reframe (grounded theory) adjudicated by Torres's interventional test.** For entangled pairs: write an explicit discrimination rule ("a record belongs to A not B when …"), blind-reassign the shared evidence against it, and check agreement — two codes are distinct iff data can be reliably assigned between them. The merge/split call is decided by the competency question "name a solution that addresses A but not B" (Grüninger & Fox style); no such solution ⇒ merge; a clean partition ⇒ keep both and rewrite each from its own evidence so its statement carries its differentia — which is precisely the operator's asked-for operation, "rephrased from the evidence of both into two totally separate ideas."

**Authoring constraints worth adopting alongside (cheaper than the pass, prevent the debt):** BFO's disjoint-siblings + genus-differentia discipline (every new sibling states what separates it from the others); Ulwick's controlled outcome-statement grammar to normalize phrasing before any comparison; Torres's moment-anchored top level as the MECE frame.

Key sources: producttalk.org/opportunity-mapping · producttalk.org/prioritize-opportunities · Ganter & Wille, *Formal Concept Analysis* · Guarino & Welty, OntoClean (loa.istc.cnr.it) · Grüninger & Fox competency questions · SemDeDup (arXiv 2303.09540) · constant comparative method + intercoder reliability (Glaser & Strauss lineage) · Ulwick, ODI job maps (strategyn.com).

## Shipped (stage 2 — the evidence-extent verdict)

Built and merged to main as PR #101 (commit ec522d1, 2026-08-11), on the operator's direct mandate. `src/ost/extent.ts` computes every Opportunity's evidence extent (the stored records its whole subtree cites) and applies the FCA/Torres verdicts as three hygiene rules on the near-duplicate channel, siblings-only: `shared-extent` (identical extents — merge, or name a solution addressing one alone), `subset-extent` (strict subset — a child mis-hung as a peer, re-hang it), `entangled-extent` (crossing overlap ≥ 0.5 — rewrite each node from its own evidence so each statement carries its differentia). All three block `done`, clear by annotation, and resolve by judgement between `ost_merge_nodes` and `ost_edit_node`; the ruleset and /ost-pass now state the discipline. Performance holds the wall-clock budget by clustering identical extents and posting-list candidate generation (the naive all-pairs form was caught by the instrument at 2423ms on the 10,000-node fixture). Pinned by 8 tests in `test/ost/extent.test.ts`.

Stages 1 and 3 remain open, deliberately: stage 1 (embedding-similarity screening) needs an embedding capability this closed tool surface does not hold — it would nominate differently-worded duplicates whose extents are disjoint because mapping created a fresh node per record, which is the case set arithmetic cannot see and the meta vault's 124-record queue exemplifies. Stage 3 (the constant-comparative reframe itself) is judgement work the pass now performs when an `entangled-extent` issue fires, per the /ost-pass instructions; whether it does so well is measurable once the first flags land.

## History
- 2026-08-11 status: (none) → shipped — Stage 2 (evidence-extent verdict) merged to main 2026-08-11 as PR #101 (commit ec522d1); pinned by test/ost/extent.test.ts. Stage 1 (embedding screen) blocked on an embedding capability the tool surface lacks; stage 3 (reframe) is now pass discipline whose quality is unmeasured.

## First live use of stage 2, and one behaviour diverged from this node's description — 2026-08-11

The twelve extent flags this mechanism raised on its first day were each adjudicated by the unattended sweep (Torres's interventional test, verdicts recorded as annotations on the flagged nodes — all twelve distinct-with-shared-provenance, zero merges, zero re-hangs; see the assumption "Extent flags mostly point at real duplicates, not at distinct needs sharing a source" beneath this node). The Shipped section above says the three rules "clear by annotation." After all eight flagged nodes were annotated, `ost_next_work` still reports the same twelve issues. Either clearing requires a form these annotations do not have, or the clear-by-annotation behaviour did not ship as described. Whichever it is, the flags currently block `done` with no path a pass can clear them by, which converts each false-positive flag into a permanent cost rather than a one-time adjudication. Worth a builder's eye before the next sweep re-pays the same twelve adjudications.

_First-party observation from the 2026-08-11 unattended sweep's own tool calls: eight `ost_annotate` writes followed by a re-run of `ost_next_work` showing `hygieneIssues` unchanged at 12. Grounds feasibility of the shipped stage, not demand. No rung change._
