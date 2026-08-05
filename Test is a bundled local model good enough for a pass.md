---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-22-agent-as-driver.md'
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/product/offline-trial-pass.test.ts
---
#AssumptionTest #ported-from-ost-agent-vault #evidence/assertion

**Risk category: Feasibility.** Riskiest assumption: a small bundled/local model produces a maintenance pass good enough to be worth shipping as the zero-credential trial path.

**Proposed test (small, fast):** Run the local model against the golden evaluation set and compare faithfulness/shape-correctness to a frontier driver.

**Pre-committed success threshold:** local model reaches ≥70% of frontier faithfulness score with no invalid-shape nodes (e.g. solution-as-opportunity) above an agreed rate.

_Proposal only — a human runs this evaluation. Unvalidated._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 instrument: (none) → npx vitest run test/product/offline-trial-pass.test.ts — Asserts the node's actual promise — a first-time user running the tool end-to-end with no external account and no network at all: a full maintenance pass completes with the network disabled and no credential in the environment. Red today because the deterministic CLI works offline but every reasoning step is supplied by the connected session's model, so a pass cannot complete without one.
