---
type: Assumption
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — the belief this solution's test was already
  measuring
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Test is read-only GET access enough to gather needed evidence]]

Structural inability to write back is the safety guarantee. It costs nothing only if GET-only access actually reaches the evidence — if the useful data sits behind a search or an export that needs a write, the guarantee has been bought by making the integration useless.
