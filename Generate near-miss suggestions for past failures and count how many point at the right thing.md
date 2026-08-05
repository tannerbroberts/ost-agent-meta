---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: At least 60% correct and at most 1 in 10 actively misleading.
instrument: npx vitest run test/cli/path-near-miss.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that suggestions are more often right than misleading. A caller told "did you mean this other directory" will sometimes say yes when the real answer is that what they wanted does not exist and something is wrong upstream — and a helpful suggestion is how that goes unnoticed.

**Risk category: usability.**

**Design.** For every failed path lookup in the transcripts, generate the near-miss suggestion. A person who knows what the caller was actually after marks each as correct, unhelpful, or actively misleading. The misleading count is the one that decides this.

**Why it is small.** The failures exist and the intent is usually visible in the surrounding session. Generating suggestions is a few lines.

**What it will not cover.** Whether a caller would accept a wrong suggestion is a separate behavioural question this does not touch. The rate is a precondition, not the whole answer.

A human marks these and records the result.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/cli/path-near-miss.test.ts — Feeds the recorded failed path lookups in and asserts the suggested nearest existing path is the one that was meant; fails today because a failed lookup returns only the error.

## Instrument Log
- 2026-08-04 **red** (exit 1) `npx vitest run test/cli/path-near-miss.test.ts` — No test files found, exiting with code 1
- 2026-08-05 **green** (exit 0) `npx vitest run test/cli/path-near-miss.test.ts` — Duration  1.76s (transform 88ms, setup 0ms, collect 138ms, tests 1.43s, environment 0ms, prepare 31ms)
