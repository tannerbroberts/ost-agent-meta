---
type: Assumption
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — the belief this solution's test was already
  measuring
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Check that a recorded exit code cannot clear a gate or masquerade as a result]]

The split holds only if the recorded exit code stays inert — written to the instrument log, never to Results, never moving a status. If anything downstream reads an exit code as evidence, the runner has quietly granted itself the authority the split exists to withhold.
