---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  The rewrite is at most 3× the original length and the reader says they would
  still edit it.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that the transparency cost is acceptable. Some helpers exist precisely because they are five lines of shell anyone can read and edit, and rewriting those makes them longer, more opaque, and harder for the operator to change.

**Risk category: usability.**

**Design.** Take the shortest existing helper and rewrite it against the runtime the project already ships. Compare line count, and then show both versions to someone who uses these helpers and ask which they would be willing to edit if it did something slightly wrong at two in the morning.

**Why it is small.** One helper, one rewrite, one conversation.

**What it will not cover.** The shortest helper is where the rewrite looks worst, which makes this a deliberately unfavourable case. A longer helper would likely rewrite well, and the honest reading is about where the crossover sits rather than a single verdict.

A human runs the comparison and records the result.
