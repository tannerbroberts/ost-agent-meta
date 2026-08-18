---
type: Opportunity
source: >-
  INBOX:friction/2026-08-01-friction-wall-clock-budget-test-flaked-a-second-time-2280.md
created: '2026-08-02'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[My performance gate is an absolute number, so a busy machine alone can fail it]]
[[I hand-exclude the flaky test on every run, and the green that comes back never says what it skipped]]
[[One red run is all I get, and nothing in it separates noise from a real break]]
[[A perf gate reports its measurement next to the number the criterion recorded]]
[[Three gates fired correctly in one session and every one of them read as noise first]]
[[State timing gates as work completed rather than wall-clock, so a busy machine cannot fail one]]

**The need (operator's voice):** "My gate went red. I cannot tell from the record whether I broke the product or whether the box was busy, so I have to re-run it by hand to find out — and if I stop bothering to check, the day it means something I will wave it through."

**What was observed (two confirmed occurrences):** `test/mcp/wall-clock-budget.test.ts` asserts a hard-coded millisecond ceiling. On the twentieth scheduled pass `ost_next_work` took 2004ms against a 2000ms budget inside the full 141-file suite, then passed at 18077ms of margin re-run in isolation seconds later. On the twenty-first pass the same test failed again at 2280ms and again passed in isolation. Same shape, same cause both times: zero tolerance for suite-level CPU contention on a shared sandbox, with no code regression behind either failure.

**Why it matters:** The whole value of an unattended gate is that its verdict can be trusted without a human re-deriving it. A threshold that fires on machine load spends the operator's scarcest resource — attention they do not have (see "I need the tree's output to be actionable by compute alone, because my hours don't exist") — and it trains the reader to discount red. The second occurrence is what makes this an opportunity rather than a one-off: the twentieth pass's own filing named a repeat as the thing worth a human's eye rather than routine re-filing.

**Distinct from its neighbours:** "My tests carry thresholds nobody ever fixed, so nothing can come out a failure" is the absence of a committed threshold, so nothing can come out red. This is the opposite failure — a threshold that is committed but not robust, so red carries no information. "A failed pass reports success, so my automation can't tell" is a false pass; this is a false fail.

**Litmus test:** More than one way to address it — express the budget as margin relative to a same-run baseline rather than absolute wall-clock; assert on work units (calls, file reads) instead of time; retry-and-confirm before reporting red; record machine load alongside the verdict so a reader can attribute it; isolate timing-sensitive tests from the contended suite; quarantine the assertion into a separate advisory lane. Real trade-offs between them. Passes.

**Evidence rung:** `assertion` — the source is the agent's own friction filing. No external party involved; floor rung per the ladder's rule.

## Evidence — the first occurrence (mapped 2026-08-02)

`INBOX:friction/2026-08-01-friction-wall-clock-budget-test-flaked-once-ost-next-work.md` — kind `slow`, filed 19:30Z, one hour before the filing this node is sourced to. `ost_next_work` took 2004ms against the 2000ms budget inside the full 141-file suite, then passed at 18077ms of margin re-run in isolation seconds later. Filed with the cause already correctly identified: "a hard-coded ms threshold with no tolerance for suite-level CPU contention, so it can fail on a shared sandbox without any code regression."

The pair matters more than either filing alone. A single flake is noise a reasonable person ignores; two in consecutive passes, with the same test, the same shape and the same isolation-passes result, is a property of the gate rather than of the machine. The twentieth pass's filing pre-committed the escalation — a second occurrence was to be treated as worth a human's eye rather than routine re-filing — and the twenty-first delivered it. That pre-commitment is why this reached the tree instead of becoming a third identical friction note.

## Corroborating provenance

- `TRANSCRIPT:97546e2f-307a-46c7-a40e-64de3ec75f68` (2026-07-30, machine-recorded): a session in which `npx vitest` came back **exit code 143 with "Tests 1 failed (1)"**. 143 is SIGTERM — the run was killed, not failed — and the line the agent read said only that a test failed. This is the confusion this opportunity names, captured mechanically rather than recalled: the exit code that means "the machine took the process away" and the exit code that means "your change is wrong" arrived in the same shape, in the same sentence, and the session treated it as a real failure.
- Same session also shows `(eval):1: == not found` and a refused `sleep 45` — both filed against other opportunities; only the 143 belongs here.

Evidence class stays `assertion` for this node overall: the trace observes the agent's own run, not an outside user's.

## History
- 2026-08-05 unlinked "Budget against a same-run baseline instead of against the clock" — re-parented under "One red run is all I get, and nothing in it separates noise from a real break" — this solution answers that need, not the categories beside it
- 2026-08-05 unlinked "Assert on work units instead of milliseconds" — re-parented under "One red run is all I get, and nothing in it separates noise from a real break" — this solution answers that need, not the categories beside it
- 2026-08-05 unlinked "Re-run once and report the disagreement rather than the first result" — re-parented under "One red run is all I get, and nothing in it separates noise from a real break" — this solution answers that need, not the categories beside it

## Observed corroboration — 2026-08-05 sweep

Two machine-recorded session traces show this failure in its pure form, and neither needed a person to notice it:

- `TRANSCRIPT:97546e2f-307a-46c7-a40e-64de3ec75f68` — a Bash test run returned **exit code 143** alongside the text `Tests 1 failed (1)`. 143 is SIGTERM: the run was *killed*, not failed. The surface the agent read said "1 failed" and nothing distinguished the kill from a defect.
- `TRANSCRIPT:516fdfb8-bab1-41a4-b1e5-92fde97bd90d` — a CI poll returned **exit code 8** for `bundle-drift` while a sibling job read `test pending 0`. One job had a verdict, one had not run, and the aggregate exit code carried both.

This is observed behavior from the agent's own sessions rather than an outside report, so it grounds the usability half of this opportunity and not the desirability half. What it adds is that the confusion is not hypothetical and not rare: the signal that would separate the two — the signal number, and whether a job reached a verdict at all — was present in the raw output and absent from what the agent acted on.

## Corroboration — a transient upstream 503 read the same as a real failure (unattended sweep, 2026-08-17)

`TRANSCRIPT:09ec7cd2-2b93-4f4a-8942-319456e8ce11` recorded three consecutive Bash calls returning `Exit code 1 … HTTP 503: No server is currently available to service your request. Sorry about that. Please try resubmitting your request and contact us if the problem persists. (https://api.github.com/graphql)`. Each surfaced as a plain exit-code-1 tool_error, indistinguishable in shape from a call that failed because the request itself was wrong — the same confusion this node names, this time at the network layer rather than the process-signal layer the prior corroboration recorded.

_Source: `TRANSCRIPT:09ec7cd2-2b93-4f4a-8942-319456e8ce11` — observed behavior, captured mechanically from the agent's own transcript. Grounds usability, not desirability.

## Additional observed instance

TRANSCRIPT:09ec7cd2-2b93-4f4a-8942-319456e8ce11 — an unattended firing hit three consecutive "HTTP 503: No server is currently available" errors from api.github.com/graphql within one session, indistinguishable at the time from a real failure in what the run was trying to do.
