---
type: AssumptionTest
status: unvalidated
evidence: assertion
source: 'INBOX:2026-07-22-adapter-reality.md'
created: '2026-07-25'
---
#AssumptionTest #ported-from-ost-agent-vault #evidence/assertion

**Risk category: Feasibility.** Riskiest assumption: read-only, GET-only access is sufficient to gather all the evidence the tree needs — no write scope is required for legitimate ingestion.

**Proposed test (small, fast):** Ingest a real project's Jira/Confluence evidence using a least-privilege read-only token and GET-only client; list anything that could not be retrieved.

**Pre-committed success threshold:** all required evidence retrievable read-only; no ingestion task needs write scope.

_Proposal only — a human runs this with real data. Unvalidated._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
