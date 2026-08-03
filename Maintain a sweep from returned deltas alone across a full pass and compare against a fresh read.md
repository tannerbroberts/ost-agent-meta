---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: The accumulated sweep matches a fresh read exactly after at least 100 writes.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that every write can compute its consequences correctly. A write that gets them wrong leaves the caller confidently out of step with the tree — a failure with no symptom until something surprising happens.

**Risk category: feasibility.**

**Design.** Over one full pass, have each write return its delta and maintain a locally accumulated sweep. Do not consult it. At the end, produce a fresh sweep from the tree and compare the two field by field. Every divergence is a write whose delta computation is wrong.

**Why it is small.** One pass, and this pass alone made over two hundred writes — a large sample from a single run.

**What it will not cover.** It assumes a single writer, which is exactly the condition under which the approach is correct. The interesting failure — drift when a second agent is writing — is invisible to this and needs a concurrent arm.
