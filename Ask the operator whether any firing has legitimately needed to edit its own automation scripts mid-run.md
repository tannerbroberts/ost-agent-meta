---
type: AssumptionTest
created: '2026-08-18'
evidence: assertion
lane: humans-required
threshold: >-
  Operator finds zero legitimate need-to-edit-automation-scripts cases in recent
  build-loop history, or finds at least one
---
#AssumptionTest #unvalidated #evidence/assertion

Small, fast check: the operator reviews recent build-loop reports for any case where a firing genuinely needed to modify an automation script to finish legitimate work (not just an unreviewed policy drift). Threshold: zero such cases in the reviewed history, or at least one.

A person outside the building is the measurement here: Whether any firing has a legitimate reason to touch the automation scripts is a policy judgment about what the operator considers "legitimate," not a fact a spec file can settle — it is the operator's own risk tolerance being asked, not the code's behavior.
