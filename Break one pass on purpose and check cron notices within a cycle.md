---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-25-friction-a-pass-that-dies-on-a-driver-error-still-exits-0.md'
created: '2026-07-25'
evidence: assertion
---
#AssumptionTest #unvalidated #evidence/assertion

**Assumption (feasibility/usability):** a nonzero exit actually propagates through the operator's real scheduling path (cron/launchd → mail/log/alert), not just the terminal.

**Method:** schedule a deliberately-broken pass (bad model name) on the operator's real machine for one cycle. Observe what, if anything, tells the human.

**Pre-committed threshold:** the failure is noticed through the scheduling path within one scheduled cycle without checking manually. If nothing surfaces, exit codes alone are insufficient and the status/supervisor siblings gain priority.

**Decides:** whether the exit-code floor is enough on its own.

*Proposed by the agent — to be run by a human. No results recorded here.*
