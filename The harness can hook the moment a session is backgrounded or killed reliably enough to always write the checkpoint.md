---
type: Assumption
created: '2026-08-18'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

Feasibility belief: there's a harness-level hook for "this session is about to be backgrounded or is being terminated" that fires reliably enough (not just on a clean exit) to guarantee the checkpoint line actually gets written before state is lost.
