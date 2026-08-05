---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-25-friction-a-pass-that-dies-on-a-driver-error-still-exits-0.md'
created: '2026-07-25'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Break one pass on purpose and check cron notices within a cycle]]

**The idea.** The smallest honest contract: a pass whose driver or any tool invocation errors exits nonzero and prints the error as the last line. Cron, launchd, CI — everything already speaks this protocol.

**Contrast with siblings:** the machine-legible floor; the status-surface sibling is for humans, the supervisor sibling for recovery. This one costs an afternoon and unblocks both.

**Trade-off:** partial passes (some work done, then an error) need a decision — fail the whole pass or exit a distinct 'partial' code.

## Built — 2026-07-25, v0.5.0

`ost-agent` commit `f091b04`. `ost-agent run` sets exit 1 on any pass error and prints `<process> FAILED: <error>` on stderr; `ost-agent schedule` logs the same line and keeps the supervisor up. The cost estimate on this node ("an afternoon") was roughly right — it was well under one, because the run journal already carried everything needed and only the exit path had to change.

**The trade-off this node flagged is now decided:** a partial pass fails whole (exit 1), no distinct partial code. Reasoning is recorded on the parent opportunity so it is visible to anyone reading the branch rather than buried here.

**Half of this node's assumption test ran mechanically as part of the build.** The regression test breaks a pass on purpose — it strips every Anthropic credential and runs `P2_map` with real evidence to map, reproducing the exact auth failure that was observed on 2026-07-25 — and asserts exit 1 with `FAILED` in the output. That is the *first* half of [[Break one pass on purpose and check cron notices within a cycle]]. The second half (does a real cron notice, within one cycle?) has not run and cannot be run by compute alone: it needs a schedule, a wall-clock cycle, and someone to confirm they were actually notified.

**Status untouched.** A passing test the agent wrote about its own build is not a validated assumption, and the agent does not record results.

## Definition of done

[[Break one pass on purpose and check cron notices within a cycle]]

```
npx vitest run test/runner/pass-exit-code.test.ts
```

Green means: the channel cron actually reads carries the truth — a pass that throws exits nonzero, one that completes exits zero, and the failing run names the phase it died in and the last node it touched. Green does **not** mean cron notices within a cycle; that needs a real scheduled run broken on purpose and a person watching the clock.
