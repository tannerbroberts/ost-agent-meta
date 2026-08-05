---
type: AssumptionTest
source: 'TRANSCRIPT:ac007b7b-ac18-4a19-94f1-cb5f3c93ca42'
created: '2026-08-05'
evidence: assertion
threshold: >-
  A set of at most 6 state questions covers every captured environment failure,
  and no failure requires a seventh.
instrument: npx vitest run test/runner/workspace-state-probe-coverage.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility.**

The assumption is that a *small fixed* set of state questions covers the failures that actually happen. That is the whole candidate: a probe is a guess about which facts will matter, and if covering real history takes twenty questions then the probe is the wrong shape and the plan should declare what it needs instead.

**Design.** Take every environment failure in the harvested transcripts — the four exit-128 `fatal:` failures in freshly-scaffolded directories, the exit-127 `tmux not found`, and the missing-path failures — and for each ask which single state question would have predicted it. Group the questions, count the distinct set, and check whether any failure needs one outside the set.

**Why it is small.** The failures are already captured. This is classification and counting against a fixed list, with nothing to build and nothing to run in anger.

**What it will not cover.** The census is bounded by failures that happened, not failures that can happen — a question absent from history may be the one that matters, and this is exactly the limit that makes the result an argument rather than a proof. It also says nothing about probe *cost*: six questions that are cheap to answer and six that each cost a subprocess are very different products, and this measures only the count.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/runner/workspace-state-probe-coverage.test.ts` — No test files found, exiting with code 1
