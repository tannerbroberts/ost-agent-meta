---
type: Solution
source: 'INBOX:2026-08-16-audit-loop-efficiency-and-checkout-drift.md'
created: '2026-08-16'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Denying Write on automation-script paths still lets the build agent finish every task it's actually asked to do]]

Scope the build agent's own `Write` permission grant to exclude `examples/automation/*.sh` (and any other path that constitutes the loops' executable policy), so a build session cannot edit the scripts that bound its own behavior even within a single firing, regardless of checkout or worktree hygiene. Orthogonal to the checkout-reset and worktree-isolation candidates beside it: those stop a bad edit from *persisting* to the next firing; this stops the edit from being *writable* at all. Requires the policy scripts to live somewhere the agent's own grant does not cover, or a permission-layer path-deny the harness enforces independent of git state.

## Issues
- 2026-08-17 Assumption surfaced ("Denying Write on automation-script paths still lets the build agent finish every task it's actually asked to do") but its test is not created: it's a feasibility question the repository can answer, and naming `humansRequired` just to satisfy the tool would misstate that. This unattended sweep holds no `ost_read_repo` grant, so it cannot ground a real instrument. Needs an attended pass (or a human) with repo sight to write the spec-file instrument.
