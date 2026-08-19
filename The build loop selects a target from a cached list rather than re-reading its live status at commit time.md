---
type: Assumption
source: 'agent-ideated:2026-08-19-unattended-sweep'
created: '2026-08-19'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Ask someone with the build loop's source open whether target selection re-reads live status or works from a cached snapshot]]

Feasibility assumption. This solution is only the right fix if the loop reads status once (e.g. at the start of a run or from a stale in-memory list) rather than immediately before committing to a target — settleable by reading the loop's own source.
