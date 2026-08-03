---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: The two labellings agree on at least 85% of items.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that "actionable by this actor right now" is decidable in a way two readers would agree on. If it is not, the predicate becomes a place to hide the same ambiguity, and a loop reading it will be exactly as confused as before while sounding more certain.

**Risk category: feasibility.**

**Design.** Take one full sweep from this vault — every outstanding item across every bucket — and have two people independently label each as actionable by an unattended pass or not, working from the ruleset alone and without conferring. Compare, and read every disagreement to see whether it is a rule that needs stating or a genuine judgement call.

**Why it is small.** One sweep, two readers, an afternoon. The disagreements are the output, and they are directly usable as the specification for the predicate.

**What it will not cover.** Two readers who both know this vault well may agree for reasons a mechanical rule could not reproduce. High agreement is necessary for the predicate to be worth building and does not establish it can be written.

A human runs this and records the result.
