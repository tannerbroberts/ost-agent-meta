---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  The safe forms fully express at least 60% of all commands, and at least 80% of
  the failing ones.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that a curated set of affordances covers enough real cases. Callers reach for shell because shell does everything; if the safe forms miss the case in hand often, the caller falls back to the failing form having paid for both.

**Risk category: feasibility.**

**Design.** Take every shell command in the harvested transcripts, both the ones that failed and the ones that worked. Design a candidate set of five or six first-class forms — comparison, wait, glob, multi-line text, pipeline. Then classify every command: fully expressible in the safe forms, partly, or not at all. Weight the failures separately from the successes.

**Why it is small.** The corpus exists and the classification is mechanical once the candidate forms are named.

**What it will not cover.** Past commands were written by someone who had only shell available and shaped their intent around it. What they would have written with better forms available is not visible here.
