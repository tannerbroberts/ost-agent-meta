---
type: AssumptionTest
source: 'agent-ideation:2026-08-06-unattended-sweep'
created: '2026-08-06'
evidence: assertion
threshold: >-
  The top-ranked build unblocks at least 3x the median build's count, and the
  top decile accounts for at least 25% of all unblockings. Flatter than that and
  the ranking is refuted — do not build the graph machinery and do not run the
  operator study beneath it.
instrument: npx vitest run test/rank/unblock-leverage-distribution.test.ts
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** The whole input is the vault on disk. Nobody is the measurement, and this is precisely the test that should run before the human study beneath the same solution is commissioned.

**What it does.** Build the unblock graph over this vault's 297 assumption tests: for each candidate build, count the tests that become readable if it ships. Report the distribution — median, top decile share, max-to-median ratio. Assert non-flatness against the bar above.

**Why it is red today.** No unblock-graph computation exists in the product; `debt` counts tests per solution and `status` rolls up rungs, but nothing derives what-unblocks-what. This is mechanism-missing red rather than merely missing-file red: the thing being asserted absent is a computation, and its absence is visible in the tool surface, which reports instrument coverage but never leverage. The spec path is named from this vault's conventions rather than read off the suite, because this sweep held no repository sight — `ost_read_repo` is off the unattended surface and a direct source-tree read was refused for permissions. A human should confirm the location before trusting a green.

**A caveat on the sample that should not be waved away.** Running this against this vault measures one tree, authored largely by one agent under one ruleset. A non-flat result here is weak evidence that leverage is non-flat in a stranger's tree. Treat a green as a licence to build, not as a general finding.

**What a green does NOT settle.** Only that the numbers differ from each other. It says nothing about whether the ordering is *right*, whether an operator would follow it, or whether unblocking count is the property worth ordering by rather than merely the one that is cheap to compute. Those are what "Hand-compute unblock counts and see if the operator's pick changes" is for, and it still needs a person.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/rank/unblock-leverage-distribution.test.ts` — No test files found, exiting with code 1
- 2026-08-31 **green** (exit 0) `npx vitest run test/rank/unblock-leverage-distribution.test.ts` — Duration  274ms (transform 21ms, setup 0ms, collect 40ms, tests 4ms, environment 0ms, prepare 36ms)
