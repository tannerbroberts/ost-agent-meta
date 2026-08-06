---
type: Assumption
created: '2026-08-06'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

Feasibility. A preflight check only works if the requirement is knowable in advance. A maintenance pass branches on what `ost_next_work` returns — a sweep with no prose-only tests never needs `ost_set_instrument`, and one with no duplicates never needs `ost_merge_nodes` — so the honest required set may be small and the useful set may be most of the surface. If the two cannot be separated, the check either refuses passes that would have succeeded or passes ones that will degrade.
