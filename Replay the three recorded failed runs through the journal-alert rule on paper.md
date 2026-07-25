---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-25-friction-a-pass-that-dies-on-a-driver-error-still-exits-0.md'
created: '2026-07-25'
evidence: assertion
---
#AssumptionTest #unvalidated #evidence/assertion

**Assumption (feasibility):** run journals as they exist today carry enough to classify failure without new instrumentation.

**Method:** paper-apply the proposed rule (error field present → failed) to every journal in `.ost-agent/runs/` including the 2026-07-25 auth failure. Minutes, existing data.

**Pre-committed threshold:** 100% of known-failed runs classified failed, zero healthy runs misclassified. Any miss means the journal schema needs a machine-legible status field first.

**Decides:** whether the supervisor lane can build on journals as-is.

*Proposed by the agent — to be run by a human. No results recorded here.*
