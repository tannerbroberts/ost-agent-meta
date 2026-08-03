---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: At least 80% of failed paths fall under 4 or fewer named roots.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that a handful of named roots covers most of what a run reaches for. Anything outside them is constructed by hand exactly as before, so the coverage share is the whole value of the approach.

**Risk category: feasibility.**

**Design.** Name a candidate set of roots — project, vault, logs, home. Take every path in the harvested transcripts, both the successes and the failures, and check whether each falls under one of them. Compute coverage separately for the two groups; the failures are what matter.

**Why it is small.** Mechanical classification over paths already captured.

**What it will not cover.** A root pointing somewhere wrong produces confident, uniform, wrong paths everywhere at once — a worse failure than scattered bad guesses because it looks systematic. This measures coverage and not that risk, which needs its own check.
