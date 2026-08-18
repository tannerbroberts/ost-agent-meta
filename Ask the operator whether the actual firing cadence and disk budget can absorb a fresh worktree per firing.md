---
type: AssumptionTest
created: '2026-08-18'
evidence: assertion
lane: humans-required
threshold: >-
  Estimated per-firing worktree overhead stays under, say, 10% of a firing's
  time/disk budget at actual cadence, or exceeds it
---
#AssumptionTest #unvalidated #evidence/assertion

Small, fast check: the operator states the actual firing frequency and available disk on the scheduling host, and estimates worktree setup/teardown cost against it. Threshold: cost stays a small fraction of a firing's budget, or it doesn't.

A person outside the building is the measurement here: Firing cadence and disk budget on the actual scheduling host are operational facts only the operator has, not something derivable from this repository.
