---
type: Assumption
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — the belief this solution's test was already
  measuring
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[The CLI fallback reaches the same vault, and refuses the write half]]

The fallback is only a fallback if it operates on the same tree and produces the same readings. It becomes a hazard the moment it can write: a degraded pass with write access is doing unattended work through a path nobody designed for it.
