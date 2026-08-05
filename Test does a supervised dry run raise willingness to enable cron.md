---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-22-design-goals.md'
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/loop/dry-run-no-writes.test.ts
---
#AssumptionTest #ported-from-ost-agent-vault #evidence/assertion

**Risk category: Desirability.** Riskiest assumption: a supervised first run meaningfully increases operators' willingness to grant unattended/scheduled operation.

**Proposed test (small, fast):** With trial users, offer a guided dry-run to one cohort and not the other; measure the share that subsequently enable unattended runs.

**Pre-committed success threshold:** dry-run cohort activates unattended operation ≥20 percentage points more often.

_Proposal only — a human runs this with real operators. Unvalidated._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 instrument: (none) → npx vitest run test/loop/dry-run-no-writes.test.ts — The solution promises a dry-run mode, and a dry run that writes is not one. This asserts the mechanism the willingness question depends on: with the dry-run flag set, a full pass produces its usual plan and report while the vault's git HEAD is unchanged and no node file's mtime moves. Missing-spec red, not assertion red — no dry-run mode exists to test, so the command fails on a missing file; a builder should make it assertion red by writing the spec first against the real loop entry point. It settles nothing about willingness to enable cron, which is a person's reaction and stays with a human.
