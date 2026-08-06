---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-22-design-goals.md'
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/git/commit-provenance.test.ts
---
#AssumptionTest #ported-from-ost-agent-vault #evidence/assertion

**Risk category: Desirability.** Riskiest assumption: after an unattended run, operators will actually *use* the commit/provenance history to rebuild confidence — rather than ignore it.

**Proposed test (small, fast):** After a real unattended pass, observe/interview ~5 operators; see whether they spontaneously open the history to check what changed and why.

**Pre-committed success threshold:** ≥3 of 5 use the trail to regain confidence without prompting.

_Proposal only — a human runs this with real operators. Unvalidated._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 instrument: (none) → npx vitest run test/git/commit-provenance.test.ts — Asserts the half of this node's claim that is not yet true: that every mutation commit carries the node AND its provenance link, so the replayed diff is attributable to a source without opening the vault. Red against today's code rather than a missing file — auto-commit already ships and is atomic, but the messages it writes are of the form 'mcp: ost_append_to_node — appended to "<title>"' and name no source id at all.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/git/commit-provenance.test.ts` — No test files found, exiting with code 1
