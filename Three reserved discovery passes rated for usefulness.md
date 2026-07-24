---
type: AssumptionTest
status: unvalidated
source: 'agent:P4_assumptions'
created: '2026-07-24'
---
#AssumptionTest #unvalidated #desirability

**Assumption under test (desirability):** Reserved discovery time produces evidence a human rates as useful, rather than guaranteeing effort that goes into low-signal busywork.

**Proposed test:** Reserve one pass a week for three weeks, unspendable by build work. After each, a human rates the output on one question: "did this change what I believe about the product, or what I plan to do next?" Yes or no, no partial credit.

**Size:** three weeks, using the schedule that already exists.

**Pre-committed threshold:** ≥2 of 3 passes rated yes. Below that the budget is protecting motion rather than progress, and the sibling that constrains *what* gets built deserves the compute instead.

**Decides:** whether guaranteeing discovery volume actually raises evidence quality — the assumption on which this whole sibling set turns.

Proposed by the agent — a human does the rating; the agent must not rate its own passes. No results recorded here.
