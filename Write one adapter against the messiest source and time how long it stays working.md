---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: 'Working within 4 hours, and at most 1 intervention in the following 30 days.'
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that adapters are cheap enough to write and stable enough to keep, so that a per-source adapter is a reasonable ongoing commitment rather than a maintenance tax that grows with every source added.

**Risk category: feasibility.**

**Design.** Pick the least convenient source the operator actually holds experiment data in, write one read-only adapter for it, and record two numbers: hours to working, and days until it broke or drifted. Run it for a month and count interventions.

**Why it is small.** One adapter, not a framework. If the worst case is affordable the rest follow; if it is not, the approach is answered before any of them is written.

**What it will not cover.** A single source is a sample of one, and the operator writing the adapter knows both sides of it. A different source with an unstable API could be an order of magnitude worse, and this would not see it.
