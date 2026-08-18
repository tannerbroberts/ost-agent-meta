---
type: Assumption
source: 'TRANSCRIPT:0f28d01f-35fa-49f0-b085-89170e306ef8'
created: '2026-08-18'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Ask someone with the Monitor tool's implementation open whether a bounded until sleep primitive is addable without reopening arbitrary shell execution]]

Feasibility. Assumes a bounded wait-for-condition primitive (poll interval, timeout, one follow-up read command) can be added to Monitor without reopening the arbitrary-shell-execution risk the command_substitution refusal exists to prevent. If the two are inseparable in Monitor's current implementation, this solution is not buildable as scoped.
