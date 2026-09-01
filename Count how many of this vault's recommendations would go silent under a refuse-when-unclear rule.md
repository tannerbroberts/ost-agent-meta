---
type: AssumptionTest
source: 'agent-ideation:2026-07-26-tenth-pass'
created: '2026-07-26'
evidence: assertion
instrument: npx vitest run test/knowledge/refuse-when-unclear-suppression.test.ts
authorship: machine
---
#AssumptionTest #evidence/assertion

**The single assumption.** That refusing to recommend on an unclear source suppresses a *small* fraction of this product's advice. If it silences most of it, the solution is not a safety improvement, it is a way of turning the tool off while appearing careful.

**Proposed test.** Replay the rule over both live vaults' existing recommendation surfaces — the prose-lane declarations, the caution hints, the hygiene findings — and count, per surface, how many recommendations survive and how many are replaced by an ambiguity report. No new code beyond the counter; no node is written; nothing is classified.

**Lane: compute-only.** It reads two local vaults and counts. No credential, no outside person, no measurement of anybody's reaction. Declared in one sentence naming one lane, which is now the only form the tool will read.

**Pre-committed threshold, fixed before the count is run.** The rule survives if **at least 70%** of current recommendations still render, per surface, on both vaults. **Below 50% on either vault, this solution is killed** rather than tuned — a rule that silences half the output is a different product decision and must be argued as one, not slipped in as a safety fix. Between 50% and 70%: report and decide nothing.

**What this test cannot tell anyone.** Whether the suppressed recommendations were the *wrong* ones. A rule could silence 5% and still silence exactly the 5% that were correct and load-bearing; the count is a cost measurement, not a benefit one. Nothing here says the remaining recommendations are any good.

⚠️ Proposed only — the agent does not run tests or record results.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/knowledge/refuse-when-unclear-suppression.test.ts — The node declares one lane and means it — "Lane: compute-only. It reads two local vaults and counts. No credential, no outside person, no measurement of anybody's reaction" — and its bar is a survival rate per surface: at least 70% of current recommendations still render on both vaults, with below 50% on either vault killing the solution outright rather than tuning it. The spec applies the refuse-on-unclear-source rule across each recommendation surface separately (prose-lane declarations, caution hints, hygiene findings), counts what still renders against what is replaced by an ambiguity report, and asserts the per-surface rate, keeping the surfaces apart because a rule that leaves hygiene findings intact while silencing every caution hint would pass on a pooled number and fail the question. It fails today because the rule does not exist and neither does the counter: nothing in the repository decides that a source does not read cleanly, so there is nothing to suppress and no denominator to divide by. What it does not settle is the half that matters most and the node says so — the count is a cost measurement, not a benefit one. A rule could silence 5% and silence exactly the 5% that were correct and load-bearing, and no exit code here distinguishes that from silencing 5% of noise.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/knowledge/refuse-when-unclear-suppression.test.ts` — No test files found, exiting with code 1
- 2026-09-01 **green** (exit 0) `npx vitest run test/knowledge/refuse-when-unclear-suppression.test.ts` — Duration  539ms (transform 136ms, setup 0ms, collect 208ms, tests 130ms, environment 0ms, prepare 31ms)
