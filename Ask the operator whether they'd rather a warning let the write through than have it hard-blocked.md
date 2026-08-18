---
type: AssumptionTest
created: '2026-08-18'
evidence: assertion
lane: humans-required
threshold: >-
  Operator states a clear preference after seeing one real example of the
  current hard-reject-then-retry cost
---
#AssumptionTest #unvalidated #evidence/assertion

Small, fast check: ask the operator directly, with one real transcript example of a hard-reject-then-retry in hand, whether they'd have preferred the write to proceed with a warning instead. Threshold: operator says yes, no, or names a condition.

A person outside the building is the measurement here: This trades a safety guarantee for fewer stalled turns — a preference only the operator can state, not something a spec file can determine on their behalf.
