---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-25-friction-a-pass-that-dies-on-a-driver-error-still-exits-0.md'
created: '2026-07-25'
evidence: assertion
---
#AssumptionTest #unvalidated #evidence/assertion

**Assumption (usability):** leading with the failure makes a human actually see it.

**Method:** with one failed run in the journals, show the operator current `ost-agent status` output for 5 seconds, then the failure-first mock for 5 seconds; ask what state the system is in after each.

**Pre-committed threshold:** failure identified from the mock and missed from the current output. Any other combination kills or trivializes this solution.

**Decides:** status redesign vs exit-code-only.

*Proposed by the agent — to be run by a human. No results recorded here.*
