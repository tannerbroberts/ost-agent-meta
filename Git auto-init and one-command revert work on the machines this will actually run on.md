---
type: Assumption
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — the belief this solution's test was already
  measuring
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Test does git auto-init and one-command revert work everywhere]]

Safety by revertibility assumes git is there or can be created, and that the worst case really is one command away. A machine where init fails, or where the revert is not a single obvious command, has none of the guarantee the design is selling.
