---
type: Assumption
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — the belief this solution's test was already
  measuring
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Check past failures against the snapshot fields before building the snapshot]]

Capturing only on failure keeps the cost proportionate. The fields have to be chosen in advance, so this only works if working directory, argv, tool versions and git SHA really do account for most of what makes a failure reproducible.
