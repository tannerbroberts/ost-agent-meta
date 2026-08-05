---
type: Assumption
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — the belief this solution's test was already
  measuring
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Compare the scheduler's view of the environment against the run's]]

Moving readiness to the dispatcher only helps if the dispatcher sees the same world. A preflight that passes where the run then fails has added a check and changed nothing, and it reports the skip against the wrong thing.
