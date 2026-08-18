---
type: Solution
source: 'INBOX:2026-08-16-audit-loop-efficiency-and-checkout-drift.md'
created: '2026-08-16'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[An isolated worktree per firing prevents state leakage without adding meaningful setup cost]]
[[The scheduling harness can afford a fresh git worktree per firing without materially slowing the build loop or exhausting disk]]

Give every firing of the build and discovery loops a fresh `git worktree` checked out from `main`, instead of both loops sharing one working directory. A firing's branch, and any edit it makes to the automation scripts on that branch, is confined to its own worktree and is discarded (or merged only through normal review) when the worktree is torn down — there is no shared mutable checkout for policy to leak through between firings. Costs setup/teardown overhead per firing and disk, unlike the cheaper reset-based solution beside it, but also closes the "stuck branch left checked out" drift this opportunity was inferred from, not just the self-modification exploit.

## Issues
- 2026-08-17 Assumption surfaced ("An isolated worktree per firing prevents state leakage without adding meaningful setup cost") but its test is not created: it's a feasibility/cost question the repository can answer, and naming `humansRequired` just to satisfy the tool would misstate that. This unattended sweep holds no `ost_read_repo` grant, so it cannot ground a real instrument. Needs an attended pass (or a human) with repo sight to write the spec-file instrument.
