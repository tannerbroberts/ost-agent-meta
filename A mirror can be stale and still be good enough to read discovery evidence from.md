---
type: Assumption
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — the belief this solution's test was already
  measuring
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Test is mirror staleness acceptable versus live reads]]

Never holding live write-capable credentials during a pass is the safety win. It costs correctness in proportion to staleness — so the question is whether discovery evidence ages slowly enough that yesterday's replica answers the same as today's system.
