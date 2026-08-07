---
type: AssumptionTest
source: 'agent:ideation-2026-08-02'
created: '2026-08-02'
evidence: assertion
threshold: >-
  Of three operators told plainly that the channel can change the agent's
  behaviour while nobody is watching, at least 2 say they would enable it and
  still leave a pass running overnight. If 2 or more say it would stop them
  running unattended, the candidate is killed.
instrument: npx vitest run test/loop/checkpoint-update.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: desirability, and specifically the potential-harm check rather than the want-it check.** The assumption is that an operator would knowingly enable a channel that lets someone else change an agent already running unattended on their machine.

**Why this is the riskiest assumption under its solution.** The engineering is ordinary and the latency benefit is real; what is not established is whether the trust cost is payable at all. This tree already carries "Trust an unmonitored agent enough to walk away", "I can't leave the process running unattended without worrying" and "Fear the agent could take a destructive, irreversible action" as live opportunities, none of them answered. A push channel adds a remote capability to alter an unattended agent's behaviour, which is the same shape those nodes are afraid of, arriving as a feature. If the answer is no, no amount of checkpoint discipline saves the candidate.

**The test, small and fast.** Describe the channel to three operators in one honest paragraph — including, without softening, that an update can change how the agent behaves while they are not watching — and ask two questions: would you switch it on, and would you still leave a pass running overnight with it on. Ask the second question separately, because agreeing to a feature and continuing to leave the machine alone are different behaviours and this candidate needs both.

**Pre-committed bar (also in the `threshold` field):** at least 2 of 3 say yes to both. If 2 or more say it would stop them running unattended, the candidate is killed — not narrowed to an opt-in, because an opt-in nobody opts into propagates nothing and would leave the tree carrying a solution that cannot fail.

**What a refuted result buys, which is why it is worth running early.** It would settle the shape of this whole branch cheaply: two pull-shaped candidates already sit beside this one, and a clear no here makes the comparison a two-way rather than a three-way choice without anything being built.

**What it deliberately does not cover:** stated reaction, not behaviour. Someone saying they would enable a channel is the `stated` rung at best, and what an operator does with a real switch on a real machine is a different measurement that only exists after something is built.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/loop/checkpoint-update.test.ts — Asserts the node's one falsifiable engineering claim — that an announced update is held until between passes and never applied mid-pass, so it cannot land on a half-finished write. Red today because no update channel and no checkpoint barrier exist in the loop at all.

## Instrument Log
- 2026-08-07 **red** (exit 1) `npx vitest run test/loop/checkpoint-update.test.ts` — No test files found, exiting with code 1
