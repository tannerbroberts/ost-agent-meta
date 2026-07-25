---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-22-adapter-reality.md'
created: '2026-07-25'
---
#AssumptionTest #ported-from-ost-agent-vault

**Risk category: Feasibility.** Riskiest assumption: read-only, GET-only access is sufficient to gather all the evidence the tree needs — no write scope is required for legitimate ingestion.

**Proposed test (small, fast):** Ingest a real project's Jira/Confluence evidence using a least-privilege read-only token and GET-only client; list anything that could not be retrieved.

**Pre-committed success threshold:** all required evidence retrievable read-only; no ingestion task needs write scope.

_Proposal only — a human runs this with real data. Unvalidated._
