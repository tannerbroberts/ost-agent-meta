---
type: AssumptionTest
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
threshold: >-
  A fixture category with zero direct solutions and 45 in its subtree is absent
  from `underservedOpportunities`, AND a fixture category whose subtree total
  clears the threshold while a majority of its leaves carry zero is still
  reported.
instrument: npx vitest run test/ost/next-work-rollup-count.test.ts
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**What it measures.** Both halves of the belief, in one file. The first assertion is the fix: subtree counting silences a well-served category. The second is the falsifier: a lopsided category — plenty of solutions, all under one child — must NOT be silenced, because that is the inversion this assumption warns about.

A run that satisfies the first and fails the second is the interesting outcome, and it argues for the sibling that redirects to leaves rather than for this one.

**Why it is red today.** `underservedOpportunities` counts direct solution children only; no subtree arithmetic exists in the sweep, so neither assertion can pass.

**Honest limit on the instrument.** This pass had no repository sight — `ost_read_repo` was unconfigured and direct reads of the checkout were denied — so the named spec file does not exist and its first red will be a missing path rather than a failing assertion against the module. That is the weak form of red described in "My instruments are red because a file is absent, not because the behaviour is", and it is recorded here rather than hidden. A builder should move these assertions into whichever existing spec covers `computeNextWork` and delete this path.

**What a green here does not settle.** Nothing about whether rollup is the right fix, and nothing about whether operators find the resulting queue more useful. It settles only that the arithmetic behaves as described on a constructed tree.

## Instrument Log
- 2026-08-07 **red** (exit 1) `npx vitest run test/ost/next-work-rollup-count.test.ts` — No test files found, exiting with code 1
- 2026-09-03 **green** (exit 0) `npx vitest run test/ost/next-work-rollup-count.test.ts` — Duration  3.78s (transform 514ms, setup 0ms, collect 778ms, tests 2.58s, environment 0ms, prepare 68ms) [spec 53b7332fae09]
