---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: 'At least 9 of 10 correct, 0 wrong, and 0 markers or broken links left behind.'
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that merging can be owned safely. If an unattended pass does it, the tree has swapped a collision it can detect for a resolution it cannot check — and the second is harder to notice, which is exactly how a conflict reached a commit before.

**Risk category: feasibility.**

**Design.** Construct ten realistic conflicts between two vault branches — same-titled nodes, competing appends to one parent's links, a status changed on both sides. Have an unattended pass resolve each. A person then grades every resolution as correct, lossy, or wrong, and separately checks whether any left a conflict marker or a broken wikilink behind.

**Why it is small.** Ten conflicts constructed from real nodes, one grading pass.

**What it will not cover.** Seeded conflicts are cleaner than real ones and were designed by someone who knows what makes them hard. Real collisions arrive with worse timing and less structure.

A human grades this and records the result.
