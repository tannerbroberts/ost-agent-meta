---
type: Assumption
source: 'TRANSCRIPT:0f28d01f-35fa-49f0-b085-89170e306ef8'
created: '2026-08-18'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Ask someone with the harness's sandbox implementation open whether a per-task scoped read grant is addable without widening the sandbox generally]]

Feasibility. Assumes Monitor's working-directory read restriction can be scoped per-task to a path the task itself declared, for the task's lifetime, without generally widening what any Monitor call may read. If the restriction is implemented as a single session-wide allowlist rather than something a per-task grant can extend, this solution is not buildable as scoped.
