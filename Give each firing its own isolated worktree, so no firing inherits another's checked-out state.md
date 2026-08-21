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

## Repo sight this pass — the 2026-08-17 blocker is discharged (unattended sweep, 2026-08-21)

The Issues note above records that the first assumption's test was never written, because that sweep held no `ost_read_repo` grant and would not name `humansRequired` on a question the repository can answer. This pass held the grant, so the test is now written rather than deferred a second time.

**What the repository showed, and why it strengthens this candidate's case.** Today both loops share one working directory and `loop start` refuses a dirty tree with exit 14. What stops consecutive firings wedging each other is not isolation but an enumerated waiver — `FIRING_RESIDUE_PREFIXES` — exempting the paths a firing is known to leave: `.ost-agent/usage/events.jsonl` (written inside every tool call, never committed because the dispatcher commits only for mutating tools) and `.ost-agent/census-history/` (written by the mandatory check phase). `test/loop/firing-residue.test.ts` records what the absence of that waiver cost: a vault where every tick for seventeen hours was refused.

That is an argument this solution's body did not make. The shared checkout is not merely a place drift *can* happen — it is a place drift already happened, twice, and both times the fix was to add a path to a list. Each new mechanical record written by a non-committing path needs another entry, and nothing tells anyone it is missing until a loop stops firing. Per-firing worktrees would replace an enumeration that must be maintained with a structural property that cannot go stale, and that is a stronger claim than "closes the stuck-branch drift" — which is all this node previously argued.

## Definition of done

"Two firings in per-firing worktrees leave the shared checkout clean with the residue waiver switched off"

```
npx vitest run test/loop/worktree-isolation.test.ts
```

Named in plain quoted text rather than as a `[[wikilink]]`: that test's one backlink belongs to its parent assumption, and a second link anywhere in the vault fails `check`'s single-backlink rule.

The test empties `FIRING_RESIDUE_PREFIXES` on purpose — if isolation is real the waiver is unnecessary, and that is the sharpest available form of the claim. It measures time cost, not disk; the disk half stays with "Ask the operator whether the actual firing cadence and disk budget can absorb a fresh worktree per firing", which is properly a person's question about their own machine. Neither speaks to whether the operator wants to pay for isolation at all.

_Source: this pass's `ost_read_repo` reads of test/loop/firing-residue.test.ts and src/loop/. First-party read of committed code; grounds feasibility, not demand. No command executed, no result recorded, rung unchanged._
