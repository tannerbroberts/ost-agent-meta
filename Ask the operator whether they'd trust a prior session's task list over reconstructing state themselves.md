---
type: AssumptionTest
created: '2026-08-18'
evidence: assertion
lane: humans-required
threshold: >-
  Operator states a clear preference (list, reconstruction, or a named staleness
  condition) after seeing one real example
---
#AssumptionTest #unvalidated #evidence/assertion

Small, fast check: show the operator one real interrupted-session task list alongside what git/vault history alone would have told the next pass, and ask which they'd rather the next pass trust by default. Threshold: operator prefers the list, or prefers reconstruction, or names a condition that decides it.

A person outside the building is the measurement here: Whether a stale task list is more dangerous than helpful is a judgment call about trust in an unattended process, which is the operator's own risk tolerance, not a fact a spec file can settle.
