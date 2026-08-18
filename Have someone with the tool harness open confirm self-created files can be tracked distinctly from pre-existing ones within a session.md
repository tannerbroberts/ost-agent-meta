---
type: AssumptionTest
created: '2026-08-18'
evidence: assertion
lane: humans-required
threshold: >-
  Harness confirmed to track file-creation-this-session distinctly from
  first-write-to-existing-file, or confirmed it does not
---
#AssumptionTest #unvalidated #evidence/assertion

Small, fast check: read the tool harness for whatever tracks "files written this session" and confirm it can distinguish creation from an ordinary first write to a pre-existing file. Threshold: the distinction is tracked reliably, or it is not currently tracked at all.

A person outside the building is the measurement here: This pass holds no repo-read grant to inspect the tool harness's own session-state tracking. A person with the codebase open (or an attended pass with ost_read_repo) can check this directly.
