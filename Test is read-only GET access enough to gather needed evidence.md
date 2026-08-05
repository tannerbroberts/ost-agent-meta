---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-22-adapter-reality.md'
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/adapters/get-only-client.test.ts
---
#AssumptionTest #ported-from-ost-agent-vault #evidence/assertion

**Risk category: Feasibility.** Riskiest assumption: read-only, GET-only access is sufficient to gather all the evidence the tree needs — no write scope is required for legitimate ingestion.

**Proposed test (small, fast):** Ingest a real project's Jira/Confluence evidence using a least-privilege read-only token and GET-only client; list anything that could not be retrieved.

**Pre-committed success threshold:** all required evidence retrievable read-only; no ingestion task needs write scope.

_Proposal only — a human runs this with real data. Unvalidated._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 instrument: (none) → npx vitest run test/adapters/get-only-client.test.ts — The threshold has two clauses and only one is mechanical: "no ingestion task needs write scope". This asserts it at the client boundary — every adapter request issued during a full ingest is a GET, and an adapter that attempts POST, PUT, PATCH or DELETE is refused by the client rather than by the remote's permissions, so a token that happens to be over-scoped cannot hide the violation. Missing-spec red, not assertion red: this pass holds no repo-read grant, so the file is absent and the command fails on absence; a builder should write it against the real adapter client so it goes red on an unguarded verb. It does not settle the other clause — whether GET-only retrieval is SUFFICIENT for a real project's evidence — because that needs a real Jira/Confluence corpus, and the node already assigns it to a human running it with real data.
