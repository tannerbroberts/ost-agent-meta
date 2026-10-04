---
type: AssumptionTest
status: unvalidated
created: '2026-08-02'
evidence: assertion
threshold: >-
  At least half the work identifiable as independent would have survived a
  failing verdict untouched, across at least five recorded waits including two
  that failed.
authorship: machine
---
#AssumptionTest #desirability #unvalidated #evidence/assertion

**The assumption under test (desirability):** that there is enough genuinely independent work to make filling the wait worthwhile. If most of what an agent would do during a wait turns out to depend on the pending result, this candidate converts idle time into rework and into a foundation built on a verdict that had not arrived.

**How it would run:** take the recorded sessions that waited on a check, and for each, ask what work was done after the verdict arrived and how much of it did not depend on that verdict. Then check the failing cases specifically: when a check came back bad, would work started during the wait have survived?

**Why the failing cases carry the weight:** independence is easy to claim when the verdict is good, because nothing is tested. The rule this candidate needs — what genuinely does not depend on a pending result — can only be judged against the runs where the result was bad.

Retrospective, no build. Proposed by the agent; a human runs it and records the outcome.

## Issues
- 2026-10-04 2026-10-04 unattended sweep: humans-required in substance and has no lane label. This test is a retrospective judgement over recorded sessions: for each wait, which work after the verdict "did not depend on" it. Deciding that dependence is the measurement, and the node says itself that "a human runs it". A command could list the sessions that waited on a check. It could not judge independence, and that judgement is what the threshold is about. No instrument set. The fix is `ost-agent lane --set`, because `ost_flag_humans_required` is withheld on this surface. This is the one test among the 67 unlabelled, un-instrumented tests that had no earlier sweep note. I wrote this so the next pass can read the verdict here instead of working it out again.
