---
type: Solution
source: 'INBOX:2026-08-16-audit-loop-efficiency-and-checkout-drift.md'
created: '2026-08-16'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Denying Write on automation-script paths still lets the build agent finish every task it's actually asked to do]]
[[No legitimate firing still needs the build agent's own Write grant on the automation-script paths]]

Scope the build agent's own `Write` permission grant to exclude `examples/automation/*.sh` (and any other path that constitutes the loops' executable policy), so a build session cannot edit the scripts that bound its own behavior even within a single firing, regardless of checkout or worktree hygiene. Orthogonal to the checkout-reset and worktree-isolation candidates beside it: those stop a bad edit from *persisting* to the next firing; this stops the edit from being *writable* at all. Requires the policy scripts to live somewhere the agent's own grant does not cover, or a permission-layer path-deny the harness enforces independent of git state.

## Issues
- 2026-08-17 Assumption surfaced ("Denying Write on automation-script paths still lets the build agent finish every task it's actually asked to do") but its test is not created: it's a feasibility question the repository can answer, and naming `humansRequired` just to satisfy the tool would misstate that. This unattended sweep holds no `ost_read_repo` grant, so it cannot ground a real instrument. Needs an attended pass (or a human) with repo sight to write the spec-file instrument.

## Repo sight available this pass — grounding the feasibility question (unattended sweep, 2026-08-18)

`ost_read_repo` read `examples/automation/autonomous-pass.sh` and `examples/automation/build-pass.sh` this pass (a capability change since the 2026-08-17 note above, which held no repo grant). Both scripts scope tool access via `claude -p`'s `--allowedTools`/`--disallowedTools` flags, and both grant/deny by whole tool name only (e.g. `Bash,Edit,Write,...` / `Bash,BashOutput,KillShell,Edit,Write,...`) — neither script's current invocation demonstrates a path-scoped form like `Write(examples/automation/**)`. `autonomous-pass.sh`'s own comments describe the discipline this solution wants ("Deny beats allow in Claude Code... the two must stay disjoint") but only ever at tool granularity, for the vault-write surface, not the code-write surface build-pass.sh grants.

So the open feasibility question this assumption names — can `Write`/`Edit` be scoped to exclude specific paths within one invocation, rather than denied wholesale — is not settled by what is currently deployed; neither script currently exercises that finer grain, which is evidence of absence in the current code, not proof the CLI itself lacks the capability. Confirming it either way needs someone to consult Claude Code's own permission-flag documentation or try a path-scoped rule directly, which is outside what `ost_read_repo` (scoped to this product's repo) can settle.

_Source: this pass's own `ost_read_repo` reads of both automation scripts — first-party observation of the repository. Grounds feasibility, not desirability._

## Definition of done

"The build-pass invocation denies Write on its own automation-script paths while still granting Write elsewhere"

```
npx vitest run test/automation/build-pass-write-scope.test.ts
```

The spec reads `examples/automation/build-pass.sh` as text (the technique `test/automation/build-pass-reports.test.ts` already uses seven times) and asserts two things: that the invocation's permission flags exclude `examples/automation/**` from Write and Edit, and that the same invocation still grants Write on a non-automation path. The second assertion is load-bearing — without it a blanket `Write` deny would satisfy this and defeat the point.

Named in plain quoted text rather than as a wikilink: the test is linked exactly once, by the Assumption above it, and a second link would fail the single-backlink invariant.

This is feasibility only. Whether any legitimate firing still needs to write those paths is the sibling assumption's question, and it is with the operator.
