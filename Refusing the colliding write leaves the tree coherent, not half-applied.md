---
type: Assumption
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — the belief this solution's test was already
  measuring
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Interrupt a pass mid-plan with an outside write and see what state its accepted writes leave]]

Detection catches the write and not the reasoning. An agent whose premise was invalidated will have most of its writes accepted and one refused — leaving a partially-applied plan built on something no longer true, which is worse than colliding cleanly or waiting.
