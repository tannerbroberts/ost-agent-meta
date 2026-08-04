---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-22-agent-as-driver.md'
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/loop/ambient-driver-parity.test.ts
---
#AssumptionTest #ported-from-ost-agent-vault #evidence/assertion

**Risk category: Feasibility.** Riskiest assumption: an ambient session agent driving via MCP/CLI can complete a full maintenance pass at quality comparable to a dedicated API-keyed driver, with no safety violations.

**Proposed test (small, fast):** Run the same ~10 evidence sets through ambient-driven and API-driven passes; compare faithfulness scores and check for any out-of-allowlist action.

**Pre-committed success threshold:** ambient faithfulness within 10% of API driver; zero safety violations.

_Proposal only — a human runs this with real data. Unvalidated._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-04 instrument: (none) → npx vitest run test/loop/ambient-driver-parity.test.ts — Parity is a comparison between two trees the suite can produce itself — drive one pass over a fixture vault through the ambient path and one through the API-driver path, then assert the resulting node sets and edges match; it fails today because the ambient driver does not exist, so there is nothing to compare against.
