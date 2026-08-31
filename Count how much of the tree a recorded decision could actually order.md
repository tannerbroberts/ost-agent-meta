---
type: AssumptionTest
source: 'agent-ideated:2026-08-02-unattended-sweep-priority-order'
created: '2026-08-02'
evidence: assertion
threshold: >-
  At least 13 of the 32 under-served rows must trace to a recorded decision that
  positions them. Below 7 of 32 kills the candidate.
instrument: npx vitest run test/ost/recorded-decision-ordering.test.ts
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**The assumption under test (value / coverage):** that this vault has already written down enough governance for a decision-derived ranking to be worth reading. The candidate's guarantee — that it can never invent a priority — is worthless if the honest answer it returns is a mostly-empty list. Coverage is the assumption; the guarantee is not in doubt.

**The test:** walk the 32 currently under-served opportunities and, for each, record whether a decision already in this vault positions it — the root's Prioritization section naming it in a lane, an evidence-debt gate in its own body, a founder decision touching it, a WIP hold naming it, or a lane label. Record the citation, not just the verdict, because a row that traces to a decision nobody can locate has not really been ranked. Count the rows with a locatable citation.

**Pre-committed before running, so this can come out a failure:** at least 13 of 32 must trace to a recorded decision. Below 7 of 32 kills the candidate — at that coverage the mechanism publishes an unranked tail with a handful of rows above it, which does not answer the need this branch exists for. Between 7 and 12 is a partial result meaning the mechanism is a supplement to another candidate rather than an answer on its own, and the honest response is to build it only alongside one of the other two.

**A known bias in this test, recorded so the result is read correctly:** this vault is unusually heavily governed — four consecutive passes wrote lane and hold reasoning into the root. A pass here therefore measures the *best* case, not the typical one. A comfortable pass on this vault would still leave open whether the mechanism works on a fresh tree, which is where the parent opportunity's operator actually starts.

**What it deliberately does not cover:** whether citations render legibly, and what the mechanism should do with a row whose citations contradict each other — the distribution row is a live instance of exactly that and this test only counts it, it does not resolve it.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/ost/recorded-decision-ordering.test.ts — Asserts how much of the tree a recorded decision can order and that the remainder is left explicitly unranked; fails today because ranking covers everything regardless of whether a decision backs it.

## Instrument Log
- 2026-08-04 **red** (exit 1) `npx vitest run test/ost/recorded-decision-ordering.test.ts` — No test files found, exiting with code 1
- 2026-08-31 **green** (exit 0) `npx vitest run test/ost/recorded-decision-ordering.test.ts` — Duration  398ms (transform 104ms, setup 0ms, collect 151ms, tests 11ms, environment 0ms, prepare 28ms)
