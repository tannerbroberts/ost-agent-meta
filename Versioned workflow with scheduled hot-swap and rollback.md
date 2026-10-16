---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-24-opp-self-replacing-workflow.md'
created: '2026-07-24'
evidence: assertion
authorship: machine
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

## Issues
- 2026-10-16 2026-10-16 unattended sweep: examined for a missing instrument and deliberately left without one. Recording it because this node sorts past the 25-entry cap on `solutionsMissingInstruments`, so no earlier sweep was shown it, and it had no note. Its one belief, "Operators will accept an agent that modifies itself while unattended", is desirability about people outside the building. Its test, "Would operators accept unattended self-modification", can only be answered by asking them. The node's body names two feasibility risks: that a safe checkpoint boundary exists in every process, and that "known-good" can be judged without a human. Neither has an assumption node of its own yet. If an attended pass wants a repo-answerable test here, those two are where it would go, and they would be new assumptions rather than a rewrite of this test. What a human should do: set the existing test's lane with `ost-agent lane --set humans-required`, since `ost_flag_humans_required` is withheld on this surface. Nothing executed, no instrument, status or rung changed. `ost_check` is withheld here, so this write is unverified by design.
