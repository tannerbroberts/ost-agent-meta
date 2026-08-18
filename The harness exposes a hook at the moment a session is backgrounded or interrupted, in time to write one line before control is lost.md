---
type: Assumption
created: '2026-08-18'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

This solution depends on the scheduling/build-loop harness firing a detectable signal (a shutdown hook, a pre-backgrounding callback, a wrapped exit path) at the moment a session is interrupted or moved to the background — not just at clean completion. If no such hook exists, "the instant it happens" cannot be honored and the checkpoint would only ever fire on graceful exits, which is the case that already leaves a marker today.
