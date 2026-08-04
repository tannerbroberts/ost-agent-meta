---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-24-external-review-five-dimension.md'
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/ost/rename-link-repair.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Assumption (desirability):** renames outside Obsidian happen often enough to need detection — beyond the single known incident.

**Method:** script over both vaults' git histories for wikilink targets that vanished in the same commit a similar title appeared. Hours.

**Pre-committed threshold:** >= 2 incidents beyond the known one, else defer (this solution already ranks itself last among its siblings and questions its own existence).

**Decides:** build detection vs document 'rename inside Obsidian only' vs the quarantine path.

*Proposed by the agent-side hard-fix pass — to be run by a human. No results recorded here.*

## History
- 2026-07-24 evidence: (none) → assertion — labeled at creation intent; ost_create_node@0.1.3 silently dropped the evidence input
- 2026-08-04 instrument: (none) → npx vitest run test/ost/rename-link-repair.test.ts — Scans both vault histories for the topology a rename leaves behind and asserts each break is detected and the edge repaired; fails today because nothing infers renames from link topology.
