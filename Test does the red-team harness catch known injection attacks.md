---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-22-runtime-decision.md'
created: '2026-07-25'
---
#AssumptionTest #ported-from-ost-agent-vault

**Risk category: Feasibility (potential-harm).** Riskiest assumption: a red-team suite can be built that reliably catches capability-escalation attempts delivered through ingested content.

**Proposed test (small, fast):** Seed ~20 known poisoned-content attacks ("delete everything", "exfiltrate the token", etc.) and confirm the harness flags every one; add a deliberately vulnerable branch to confirm the harness *fails* when defenses are removed (mutation check).

**Pre-committed success threshold:** 20/20 attacks caught; the mutation branch fails as expected.

_Proposal only — a human runs/reviews this. Unvalidated._
