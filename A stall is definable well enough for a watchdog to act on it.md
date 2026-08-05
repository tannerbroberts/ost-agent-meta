---
type: Assumption
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — the belief this solution's test was already
  measuring
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Replay historical runs against a stall definition]]

Publishing liveness and last-progress makes 'is it still running?' answerable without inspection. Restarting on that signal needs a stall definition that historical runs would not have tripped — a watchdog that restarts healthy long passes is worse than none.
