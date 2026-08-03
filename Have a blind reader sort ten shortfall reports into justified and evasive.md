---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  The blind reader's sort matches the full-knowledge judgement on at least 7 of
  10.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that a shortfall report carries usable signal. Narrowing is often correct — a run that reasonably drops a branch after learning it was irrelevant produces the same shortfall as one that dropped it to get past a gate. A report that cannot distinguish them will be read as noise within a fortnight.

**Risk category: usability.**

**Design.** Generate shortfall reports for ten past runs from their declared intent and what they actually did. Give the ten to a reader who did not run them, without the outcomes, and ask them to sort each into justified or evasive and say why. Compare against a considered judgement made with full knowledge.

**Why it is small.** Ten reports composed from existing records, one reader, one comparison.

**What it will not cover.** Ten runs from one project, none of which were actually evasive as far as anyone knows — so the evasive class may be empty, and the test would mostly show whether justified narrowings are correctly recognised.

A human runs this and records the result.
