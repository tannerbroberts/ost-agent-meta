---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-24-opp-self-replacing-workflow.md'
created: '2026-07-24'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Operators will accept an agent that modifies itself while unattended]]

The agent's own processes are versioned artefacts. Updates are applied at a safe checkpoint between passes, the running system restarts onto the new version without losing its place, and a bad version rolls back to the last known-good one automatically.

**How it differs from its siblings:** changes take effect unattended, with continuity as the design goal. The other two keep a human in the adoption decision.

**Trade-off:** a self-updating system can update itself into a state that no longer updates correctly; rollback has to be the one part that never changes.

**Riskiest assumptions to test:** that a safe checkpoint boundary exists in every process (feasibility); that "known-good" can be judged without a human (feasibility); that operators will accept unattended self-modification at all (desirability).

Status: agent-originated candidate; mechanism was founder-suggested. Unvalidated.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked "Would operators accept unattended self-modification" — moved under "Operators will accept an agent that modifies itself while unattended" — the belief this test measures now has a node of its own
