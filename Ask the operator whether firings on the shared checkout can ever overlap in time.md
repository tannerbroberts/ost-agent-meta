---
type: AssumptionTest
created: '2026-08-18'
evidence: assertion
lane: humans-required
threshold: 'Operator confirms strict serialization, or confirms overlap is possible'
---
#AssumptionTest #unvalidated #evidence/assertion

Small, fast check: the operator confirms whether the scheduler ever allows two firings to have the shared checkout open at once, or strictly serializes them. Threshold: firings are confirmed strictly serial (reset is safe), or overlap is possible (reset is risky).

A person outside the building is the measurement here: The scheduler's concurrency behavior on the actual host is an operational fact only the operator has visibility into.
