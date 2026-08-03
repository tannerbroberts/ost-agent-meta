---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  Recovery within 15 minutes in every scenario, and 0 cases of releasing a live
  lock.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that stale locks can be recovered safely. Every recovery policy is either too eager, defeating the lock, or too patient, so that a crash on Friday costs the weekend — and unattended runs make both failure modes likely.

**Risk category: feasibility.**

**Design.** Implement the lock with a candidate recovery policy. Then kill a holder in each of several ways — clean termination, hard kill, a process that hangs while still holding, a machine that sleeps. For each, record how long the vault stayed blocked and whether recovery ever released a lock that was still genuinely held.

**Why it is small.** A lock is a file. The scenarios are a handful of kills, and the measurement is elapsed time plus one correctness check.

**What it will not cover.** A hung holder and a crashed one are indistinguishable from outside, and no policy resolves that. What this can establish is the cost of choosing wrongly in each direction, which is what a human needs to pick a timeout.
