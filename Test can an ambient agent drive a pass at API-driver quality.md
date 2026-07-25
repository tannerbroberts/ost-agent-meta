---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-22-agent-as-driver.md'
created: '2026-07-25'
---
#AssumptionTest #ported-from-ost-agent-vault

**Risk category: Feasibility.** Riskiest assumption: an ambient session agent driving via MCP/CLI can complete a full maintenance pass at quality comparable to a dedicated API-keyed driver, with no safety violations.

**Proposed test (small, fast):** Run the same ~10 evidence sets through ambient-driven and API-driven passes; compare faithfulness scores and check for any out-of-allowlist action.

**Pre-committed success threshold:** ambient faithfulness within 10% of API driver; zero safety violations.

_Proposal only — a human runs this with real data. Unvalidated._
