---
type: AssumptionTest
created: '2026-08-18'
evidence: assertion
lane: humans-required
threshold: >-
  Auto-read is confirmed to complete and its content is confirmed available
  before the edit is computed, or confirmed not enforceable as currently
  structured
---
#AssumptionTest #unvalidated #evidence/assertion

Small, fast check: read the Edit/Write tool implementation to confirm an inserted auto-read can complete and its content actually inform the edit call, rather than being fired-and-forgotten alongside it. Threshold: ordering is enforceable, or it isn't.

A person outside the building is the measurement here: This pass holds no repo-read grant to inspect the editor tool's own call ordering. Someone with the codebase open (or an attended pass with ost_read_repo) can settle this by reading the tool dispatch code directly.
