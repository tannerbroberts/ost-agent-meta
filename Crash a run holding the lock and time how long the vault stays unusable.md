---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  Recovery within 15 minutes in every scenario, and 0 cases of releasing a live
  lock.
instrument: npx vitest run test/git/stale-lock-recovery.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that stale locks can be recovered safely. Every recovery policy is either too eager, defeating the lock, or too patient, so that a crash on Friday costs the weekend — and unattended runs make both failure modes likely.

**Risk category: feasibility.**

**Design.** Implement the lock with a candidate recovery policy. Then kill a holder in each of several ways — clean termination, hard kill, a process that hangs while still holding, a machine that sleeps. For each, record how long the vault stayed blocked and whether recovery ever released a lock that was still genuinely held.

**Why it is small.** A lock is a file. The scenarios are a handful of kills, and the measurement is elapsed time plus one correctness check.

**What it will not cover.** A hung holder and a crashed one are indistinguishable from outside, and no policy resolves that. What this can establish is the cost of choosing wrongly in each direction, which is what a human needs to pick a timeout.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/git/stale-lock-recovery.test.ts — Drives a lock holder through the four kill shapes the node names — clean exit, hard kill, hung-but-holding, machine sleep — and asserts the node's own two bars: the vault is usable again inside fifteen minutes in every scenario, and recovery never releases a lock that is still genuinely held. It fails today because there is no vault lock and no recovery policy to exercise.

## Instrument Log
- 2026-08-04 **red** (exit 1) `npx vitest run test/git/stale-lock-recovery.test.ts` — No test files found, exiting with code 1
