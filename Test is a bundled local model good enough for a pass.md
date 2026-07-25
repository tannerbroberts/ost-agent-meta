---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-22-agent-as-driver.md'
created: '2026-07-25'
---
#AssumptionTest #ported-from-ost-agent-vault

**Risk category: Feasibility.** Riskiest assumption: a small bundled/local model produces a maintenance pass good enough to be worth shipping as the zero-credential trial path.

**Proposed test (small, fast):** Run the local model against the golden evaluation set and compare faithfulness/shape-correctness to a frontier driver.

**Pre-committed success threshold:** local model reaches ≥70% of frontier faithfulness score with no invalid-shape nodes (e.g. solution-as-opportunity) above an agreed rate.

_Proposal only — a human runs this evaluation. Unvalidated._
