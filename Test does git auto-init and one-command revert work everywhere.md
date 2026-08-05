---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-22-safety-requirement.md'
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/git/revert-fidelity.test.ts
---
#AssumptionTest #ported-from-ost-agent-vault #evidence/assertion

**Risk category: Feasibility (with potential-harm check).** Riskiest assumption: every agent action maps to a cleanly revertible commit, and git can be auto-instantiated across the environments operators actually use.

**Proposed test (small, fast):** Run a pass in each of: a fresh empty directory, an existing repo, and a machine without git preinstalled; then revert the last N commits.

**Pre-committed success threshold:** git is present/instantiated in all cases and a single revert restores the exact prior state every time.

_Proposal only — a human runs this. Unvalidated._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 instrument: (none) → npx vitest run test/git/revert-fidelity.test.ts — The load-bearing half of this node's threshold is mechanical and exact — "a single revert restores the exact prior state every time" — and it applies to a claim the whole product rests on, that every agent action maps to one cleanly revertible commit. The spec runs a pass in a fresh empty directory and again inside an existing repository, snapshots the tree before each write, reverts the last N commits with one command, and asserts byte-identical restoration, plus that auto-init produced a repository in the empty case rather than writing outside version control. It fails today because nothing asserts revert fidelity: the vault auto-commits and `test/git/` covers conflict and lock behaviour, but no spec takes a snapshot, mutates, reverts, and compares — so a write that silently escaped a commit, or a revert that left a file behind, would go unreported. What it does not settle is the third environment the node names, a machine with no git preinstalled; that one is genuinely about somebody's laptop and no exit code in this suite can stand in for it, so it stays a person's check and should be recorded separately.
