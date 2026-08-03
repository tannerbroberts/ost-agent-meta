---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  At least two thirds of the forks are reversible in under an hour, and none of
  the irreversible ones is hard to recognise in advance.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that most forks are cheap to reverse. Several of the seven were structural — deleting a command, deprecating a published package, choosing where the work happens — and a run that took a default on those and was wrong destroyed more than it saved.

**Risk category: feasibility.**

**Design.** Take the seven questions from that session plus the forks from three other sessions. For each, a person estimates what reversing the default would have cost: minutes, hours, or something that cannot be undone. Count how many fall in the cheap band.

**Why it is small.** Around fifteen forks, all recorded, and an estimate each.

**What it will not cover.** Reversal cost estimated after the fact, knowing what was chosen, will tend to look lower than it felt at the time. It also cannot say whether a run could recognise the expensive ones in advance — which is the harder question and the one that decides the design.

A human runs this and records the result.
