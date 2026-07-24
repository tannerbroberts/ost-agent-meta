---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-24-opp-self-replacing-workflow.md'
created: '2026-07-24'
---
#Solution #unvalidated
[[Would operators accept unattended self-modification]]

The agent's own processes are versioned artefacts. Updates are applied at a safe checkpoint between passes, the running system restarts onto the new version without losing its place, and a bad version rolls back to the last known-good one automatically.

**How it differs from its siblings:** changes take effect unattended, with continuity as the design goal. The other two keep a human in the adoption decision.

**Trade-off:** a self-updating system can update itself into a state that no longer updates correctly; rollback has to be the one part that never changes.

**Riskiest assumptions to test:** that a safe checkpoint boundary exists in every process (feasibility); that "known-good" can be judged without a human (feasibility); that operators will accept unattended self-modification at all (desirability).

Status: agent-originated candidate; mechanism was founder-suggested. Unvalidated.
