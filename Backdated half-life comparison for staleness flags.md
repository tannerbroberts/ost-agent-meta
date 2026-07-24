---
type: AssumptionTest
status: unvalidated
source: 'agent:P4_assumptions'
created: '2026-07-24'
---
#AssumptionTest #unvalidated #feasibility

**Assumption under test (feasibility):** A decay rate exists that flags genuinely stale nodes without crying wolf on needs that are simply stable.

**Proposed test:** Have a human mark, by hand, which nodes in a backdated sample they consider stale. Then apply three candidate half-lives — say one month, three months, a year — and compare each setting's flags against the human's list.

**Size:** an offline calculation over existing nodes plus one review session.

**Pre-committed threshold:** at least one setting catches ≥80% of the human-marked stale nodes with ≤1 false flag. If no setting clears both, staleness is not a function of time here and the mechanism should be evidence-triggered instead.

**Decides:** whether decay can be automatic, and at what rate.

Proposed by the agent — the human's stale list must be produced before seeing any setting's output. No results recorded here.
