---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-22-dogfooding-idea.md'
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/eval/judge-independence.test.ts
---
#AssumptionTest #ported-from-ost-agent-vault #evidence/assertion

**Risk category: Desirability.** Riskiest assumption: operators trust a result checked by a *separate* judge more than an agent's self-assessment — the role separation is worth the extra pass.

**Proposed test (small, fast):** Show ~5 operators the same tree framed as (a) self-checked by the proposer vs (b) checked by an independent judge; measure the trust delta.

**Pre-committed success threshold:** the independent-judge framing yields a meaningfully higher trust rating.

_Proposal only — a human runs this with real operators. Unvalidated._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 instrument: (none) → npx vitest run test/eval/judge-independence.test.ts — A judge that is secretly the proposer cannot raise trust over self-report no matter what a reader says, so independence is the precondition the whole threshold rests on. This asserts it mechanically: the judging call is issued under a distinct identity from the proposing call, its context contains the candidate but not the proposer's reasoning trace, and a configuration that routes both roles to the same session fails. Missing-spec red, not assertion red — this pass cannot read the repo, so the file is absent and the command fails on that; a builder should write it against the real eval harness so it goes red on the shared-identity path instead. It does not settle whether trust actually rises, which is a reader's judgement and stays with a human.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/eval/judge-independence.test.ts` — No test files found, exiting with code 1
- 2026-08-22 **green** (exit 0) `npx vitest run test/eval/judge-independence.test.ts` — Duration  559ms (transform 211ms, setup 0ms, collect 336ms, tests 10ms, environment 0ms, prepare 43ms)
