---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  Supporting two versions costs at most 5 conditionals, and the extrapolation to
  a year stays under 20.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that versioned rules stay maintainable. Every rule must keep working under every version anyone is still on, and the checking code accumulates conditionals for standards nobody has used in months — a cost paid forever for a disruption that happens occasionally.

**Risk category: feasibility.**

**Design.** Take the current rule set and the one before it. Implement version awareness for both and count the conditionals it takes. Then extrapolate: how many would three live versions need, and how many would the last year's tightenings have produced.

**Why it is small.** Two versions is the smallest case that shows the shape, and both already exist in the history.

**What it will not cover.** The count grows with how divergent the versions are, and two consecutive versions are the most similar pair available. This is the optimistic end of the estimate.
