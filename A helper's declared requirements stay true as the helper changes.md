---
type: Assumption
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — the belief this solution's test was already
  measuring
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Write manifests for the existing helpers and check whether they catch the failures already seen]]

Requirement declarations rot. A script that grows a `mapfile` six months after its manifest was written installs cleanly and fails at line 21 — the original problem, with an extra file to maintain.
