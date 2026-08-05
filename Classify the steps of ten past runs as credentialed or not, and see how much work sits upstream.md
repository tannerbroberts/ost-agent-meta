---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  In at least 6 of 10 runs, half or more of the steps are independent of any
  credentialed step.
instrument: npx vitest run test/loop/credentialed-step-independence.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that a useful amount of a run's work is independent of its credentialed steps. If most of what a run does sits downstream of one push or one authenticated read, reordering buys nothing and the run still ends with almost nothing accomplished.

**Risk category: feasibility.**

**Design.** Take ten completed runs from the journals. Classify every step as needing the operator's credential or not, and build the dependency order. Compute, per run, what fraction of the steps could have been completed before the first credentialed step blocked anything downstream of it.

**Why it is small.** Analysis of records that already exist, no build, and it produces a distribution rather than an anecdote.

**What it will not cover.** Past runs were written by an agent that stopped at the first block, so their step order reflects that habit. A run designed to defer credentialed work might sequence itself quite differently, and this cannot see that counterfactual.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/loop/credentialed-step-independence.test.ts — Everything this test needs is already in the journals and the bar is one count — "In at least 6 of 10 runs, half or more of the steps are independent of any credentialed step" — with the node itself saying it is "analysis of records that already exist, no build". The spec reads ten completed runs from `.ost-agent/runs/`, labels each step as needing the operator's credential or not, builds the dependency order over those steps, computes per run the fraction completable before the first credentialed step gates anything downstream, and asserts the 6-of-10 bar over the resulting distribution rather than over an average, because the node asks for a distribution and a mean would hide the runs where nothing was independent. It fails today because no code partitions a run's steps by credential need: the journal records what ran and whether it errored, and nothing marks a step as credentialed or derives which steps sit downstream of one, so there is no fraction to compute. What it does not settle is the counterfactual the node names — past runs were written by an agent that stopped at the first block, so their step order already reflects that habit, and a run designed to defer credentialed work might sequence itself quite differently than this replay can see.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/loop/credentialed-step-independence.test.ts` — No test files found, exiting with code 1
