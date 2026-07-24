---
type: AssumptionTest
status: unvalidated
source: 'agent:P4_assumptions'
created: '2026-07-24'
---
#AssumptionTest #unvalidated #desirability

**Assumption under test (desirability, with a usability half):** The changes the agent proposes to its own rules are ones a human would accept — and reviewing one is genuinely cheaper than writing it.

**Proposed test:** Have the agent draft five workflow changes from friction it has actually logged, each with the evidence attached. A human reviews each, marks it accept / accept-with-edits / reject, and notes the review time. For two of the accepted ones, the human also estimates how long writing it from scratch would have taken.

**Size:** one drafting pass plus an hour of review.

**Pre-committed threshold:** ≥2 of 5 accepted as-is or with minor edits AND median review time under 5 minutes AND clearly below the write-from-scratch estimate. Proposals that take as long to review as to write have no reason to exist.

Proposed by the agent — a human does all reviewing and accepting. The agent must never adopt its own proposal. No results recorded here.
