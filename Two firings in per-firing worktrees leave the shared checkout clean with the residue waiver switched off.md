---
type: AssumptionTest
source: 'INBOX:2026-08-16-audit-loop-efficiency-and-checkout-drift.md'
created: '2026-08-21'
evidence: assertion
threshold: >-
  With FIRING_RESIDUE_PREFIXES emptied, 2 consecutive firings in per-firing
  worktrees leave the shared checkout at 0 dirty paths and both `loop start`
  calls exit 0; setup+teardown adds at most 5s per firing against the
  shared-checkout baseline.
instrument: npx vitest run test/loop/worktree-isolation.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption above has two halves — isolation works, and it is cheap — and this test measures both against one bar, because a worktree scheme that is clean but slow and one that is fast but leaky both fail the solution equally.

**What the repository says today, which is what makes the first half falsifiable rather than obvious.** Both loops share one working directory, and `loop start` refuses a dirty tree (exit 14). What keeps consecutive firings from wedging each other is not isolation — it is a hard-coded waiver, `FIRING_RESIDUE_PREFIXES`, exempting the paths a firing is known to leave behind: `.ost-agent/usage/events.jsonl`, written inside every tool call by `withUsageTracing` and never committed because the dispatcher commits only for mutating tools, and `.ost-agent/census-history/`, written by the mandatory check phase. `test/loop/firing-residue.test.ts` documents both, and documents what happened without them: a vault where "every tick for the next seventeen hours was refused with exit 14."

That list is the leakage this solution proposes to make structural instead of enumerated, and it gives the test its sharpest form: **if per-firing worktrees really isolate state, the waiver becomes unnecessary.** So the spec empties `FIRING_RESIDUE_PREFIXES` and requires two consecutive firings to still start. That is a much stronger assertion than "the shared checkout looks clean", because it fails the moment any residue path this scheme did not anticipate reaches the shared tree — including ones nobody has met yet.

**Pre-committed bar, fixed before anything runs.** With the waiver list empty: run two consecutive firings, each in its own worktree; the shared checkout must report 0 dirty paths and both `loop start` calls must exit 0. For cost, measure setup plus teardown against the shared-checkout baseline on the same machine and require at most 5 seconds added per firing. The 5s is this pass's proposal, not the operator's, and it is the number most worth arguing with — at an hourly cadence it is negligible and the bar is nearly free to clear, so a human who wants this to bite should lower it before anyone builds to it.

**What a green here does not settle.** Disk. A fresh worktree per firing consumes space proportional to cadence times retention, and this test measures time, not bytes — that half stays with the sibling test "Ask the operator whether the actual firing cadence and disk budget can absorb a fresh worktree per firing", which is correctly a person's question because it is about the operator's actual machine. It also says nothing about the self-modification exploit the parent opportunity was inferred from: a firing confined to its own worktree cannot leak a script edit forward, but proving that needs a test about what gets merged, not about what gets left behind.

**Instrument honesty, stated rather than hidden.** This is a `no-spec` red: `test/loop/worktree-isolation.test.ts` does not exist, so the command fails today for the weakest available reason. That is forced, not chosen — `ost_set_instrument` accepts only a bare `npx vitest run <path>.test.ts` and refuses any test-name filter, so an assertion-specific red inside an existing spec cannot be written on this surface (measured this pass; recorded on "My instruments are red because a file is absent, not because the behaviour is"). Two things make it as strong as that grammar allows: the path sits in `test/loop/`, a directory holding thirty-two sibling specs, so the builder inherits its conventions and its fixtures; and the spec has a direct model to work from in `test/loop/firing-residue.test.ts`, which already drives `loop start` end to end through `spawnSync` and already asserts on `workingTreeStatus` and `entriesRequiringAHuman` — the two functions this test needs.

⚠️ Proposed only — the agent does not run tests or record results.
