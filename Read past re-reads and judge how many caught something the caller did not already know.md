---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  Fewer than 10 of the 82 re-reads surfaced a change the caller could not have
  predicted.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that the re-reads were not doing real work. Trading correctness for a cheaper trace is the wrong direction if they were, and nothing so far establishes that they were not.

**Risk category: viability.** This is the question that should be answered before any of the three options here is built.

**Design.** Take the day with 82 sweep calls. For each, compare what it returned against what the previous one returned. Count the re-reads that surfaced something new, and among those, how many were changes the caller itself had just caused as against changes it could not have predicted.

**Why it is small.** The traces record every call, and the tree's history records what changed between them.

**What it will not cover.** A re-read that returned nothing new still bought certainty, and certainty has value this cannot price. The count of genuinely unpredictable changes is the more decisive half.
