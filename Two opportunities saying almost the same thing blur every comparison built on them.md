---
type: Opportunity
source: 'CONVO:2026-08-11 operator session'
created: '2026-08-11'
evidence: stated
---
#Opportunity #unvalidated #evidence/stated
[[A decorrelation pass embedding screen, then evidence-extent verdict, then constant-comparative reframe]]

**The need (operator's voice, 2026-08-11):** "We should have strong decorrelation operations between opportunities. If one opportunity has significant overlap with another, it ought to be rephrased from the evidence of both into two totally separate ideas." The operator also asked whether accepted ontologies of concepts — or a proven method for constructing rigorous ontologies of opportunity concepts — exist.

**Why it matters:** prioritization only ever compares siblings; two entangled siblings make that comparison meaningless, and every downstream ideation and assumption inherits the blur. Torres's own distinctness criterion is interventional, not verbal: siblings must be "distinct — you can address one without addressing another" (producttalk.org/opportunity-mapping). Two opportunities are really one when solving either necessarily solves the other.

**What is true today (measured):** overlap detection is title-token Jaccard ≥ 0.7, same layer only (`src/ost/dedupe.ts`), surfaced as a `near-duplicate` hygiene issue. It cannot see semantic overlap under different wording — `docs/reference/v1-readiness.md:3185` records two names for the identical work item scoring 0.29 — and the live loop log's own diagnosis of the evidence queue is "every record restates one of four needs the tree already names; mapping them would add ~120 duplicate opportunities." The word "decorrelation" appears nowhere in the repo. `ost_merge_nodes` exists and is granted to the pass, so the resolution half is built; the detection and reframing halves are not.

**The research answer (2026-08-11 literature pass; sources in the child solution):** yes, rigorous methods exist. The strongest fits for opportunity nodes: Formal Concept Analysis (same evidence-extent ⇒ same concept; subset extent ⇒ parent/child not sibling), grounded theory's constant comparative method (two codes are distinct iff data can be reliably assigned between them; chronic cross-assignment ⇒ write a discrimination rule or merge), and Torres's sibling test recast as a competency question ("name a solution that addresses A but not B"). OntoClean, BFO's disjoint-siblings/genus-differentia discipline, and Ulwick's controlled outcome grammar transfer as authoring constraints rather than as a pass.

**Litmus:** several distinct directions — evidence-extent set arithmetic, embedding-screen-then-adjudicate pipelines, authoring-time differentia requirements, periodic constant-comparative re-coding. A real opportunity.
