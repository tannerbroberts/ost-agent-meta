---
type: AssumptionTest
source: 'agent:ideation-2026-08-03'
created: '2026-08-03'
evidence: assertion
threshold: >-
  Fewer than 5 of the last 100 recorded steps would have been refused; and of
  those refused, none is a failure anyone later acted on.
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: viability** — specifically, whether the cure costs more than the disease. This solution deliberately throws information away: a failure with unknown context is still a signal that something broke, and refusing to record it loses that. The question is how often that happens.

**The test.** Take the last hundred recorded steps. Determine, for each, whether the recorder could have established its context. Count how many would have been refused. Then take that refused set and check the second condition: did anyone act on any of them later — a fix, an issue, a follow-up commit? A refused record that someone used is a signal this rule would have destroyed.

**Why there are two conditions.** A low count alone is not enough. If the five refused records happen to be the five that mattered, the rule is bad even at 5%. The second condition is what makes this a real test rather than a rate.

**Why the threshold is strict.** This is the cheapest of the three siblings and its whole claim is that it costs nothing real. A rate above 5% means it is not a cheap safety net, it is a policy change with consequences, and the middle version named in the solution body — record it but mark it `context-unknown` and exclude it from any count implying reproducibility — becomes the better candidate.

**A likely outcome worth pre-committing to:** if the count is very low, this is worth shipping *regardless* of what the other two siblings do, because it is nearly free and they do not cover the same failure.

Proposed, not run. Recording a result is a human's `ost-agent result`.
