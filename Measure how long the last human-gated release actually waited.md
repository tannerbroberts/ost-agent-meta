---
type: AssumptionTest
source: 'agent-ideated:2026-08-02-maintenance-pass'
created: '2026-08-02'
evidence: assertion
instrument: npx vitest run test/release/human-gate-latency.test.ts
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: viability.** What a human gate costs in latency, measured on this operator rather than assumed about operators in general.

**The assumption under test.** That a mandatory human tagging step is an acceptable price for eliminating the second release train. The candidate is skeptical of itself and names the reason: this project already has a human gate on publishing, and the evidence suggests it does not clear quickly. The lazy MCP server was finished on 2026-07-26 and, per its own builder note, could not reach any consumer until `npm publish` ran — blocked on the credential only the founder holds. Formalising a second human gate on a path already stalled at one may simply be the current failure, renamed.

**The test (measure what already happened, ask nobody for anything).** For every artefact in this project that has waited on a human action — the unpublished release, the `ost-agent result` filings sitting unrun across 99 assumption tests, the three paste-ready verdict commands a briefing recorded as unrun for four briefings — record two dates: when the artefact became ready, and when the human acted. Compute the wait. Where the human has not yet acted, record the wait as **still open** with its running duration, and count it, because open waits are the finding rather than missing data.

**Pre-committed threshold.** **Median human-gate latency at or under 7 days, with fewer than 25% of gates still open**, and this candidate is viable. Above that, it is closed — not because a single release train is wrong, but because this operator cannot be the gate, and the honest form of the idea becomes a *different* candidate: a single autonomous train with a human veto after the fact rather than a human action before it.

**Why this is the right test even though it looks like a detour.** It measures the one variable that decides the candidate, it needs no build, no publish rights and no new instrumentation, and the data is already on disk. It also produces a number this tree needs for reasons well beyond this branch: every solution that puts a human on the critical path is making the same bet, and none of them have priced it.

**Who runs it.** A human — and the number will be about them, which is worth saying plainly since it makes the test uncomfortable to run and easy to defer. If it is deferred, that deferral is itself a data point for the same question.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/release/human-gate-latency.test.ts — The node's own design says the data is already on disk and nobody is asked for anything — "measure what already happened, ask nobody for anything ... it needs no build, no publish rights and no new instrumentation" — and its bar is two statistics: median human-gate latency at or under 7 days, with fewer than 25% of gates still open. The spec enumerates every artefact in the project that waited on a human action (the unpublished release, the unrun `ost-agent result` filings across the vault's assumption tests, the paste-ready verdict commands recorded in `.ost-agent/drafts/`), takes the ready-date from git and the acted-date from the recording that closed it, computes the median, and counts still-open waits with their running duration as the node requires — because open waits are the finding rather than missing data, and a computation that dropped them would report a flattering median. It fails today because nothing in the repository knows what a human gate is: no code pairs a became-ready timestamp with a human-acted timestamp, so there is no latency series to take a median of. What it does not settle is generality — the number is about one operator, which the node states plainly, and a median over this project's gates says nothing about whether a human gate is affordable for anyone else.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/release/human-gate-latency.test.ts` — No test files found, exiting with code 1
- 2026-09-02 **green** (exit 0) `npx vitest run test/release/human-gate-latency.test.ts` — Duration  225ms (transform 19ms, setup 0ms, collect 17ms, tests 4ms, environment 0ms, prepare 26ms) [spec 4db54d052b3e]
