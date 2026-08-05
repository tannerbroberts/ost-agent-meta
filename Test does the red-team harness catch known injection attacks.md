---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-22-runtime-decision.md'
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/security/injection-red-team.test.ts
---
#AssumptionTest #ported-from-ost-agent-vault #evidence/assertion

**Risk category: Feasibility (potential-harm).** Riskiest assumption: a red-team suite can be built that reliably catches capability-escalation attempts delivered through ingested content.

**Proposed test (small, fast):** Seed ~20 known poisoned-content attacks ("delete everything", "exfiltrate the token", etc.) and confirm the harness flags every one; add a deliberately vulnerable branch to confirm the harness *fails* when defenses are removed (mutation check).

**Pre-committed success threshold:** 20/20 attacks caught; the mutation branch fails as expected.

_Proposal only — a human runs/reviews this. Unvalidated._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 instrument: (none) → npx vitest run test/security/injection-red-team.test.ts — This node's threshold is already two exit codes wearing prose: "20/20 attacks caught; the mutation branch fails as expected." Both halves are mechanical over content this project generates itself — a seeded corpus of poisoned ingest notes ("delete everything", "exfiltrate the token", and the rest of the twenty) driven through the ingest path, asserting the harness flags every one, plus a mutation control that disables the defence and asserts the suite goes red, which is the half that stops the harness from passing by looking at nothing. It fails today because no such corpus and no such harness exist: `test/security/` holds an allowlist-registration audit, and nothing in the repository feeds hostile ingested content through the reader that treats fetched text as DATA. Writing this as a spec rather than a study is the point — an injection defence tested by a person reading twenty notes is tested once, and one tested by a command is tested on every commit. What it does not settle is coverage: twenty attacks somebody thought of is not the attack surface, and a green here says the known twenty are caught, never that the twenty-first is.
