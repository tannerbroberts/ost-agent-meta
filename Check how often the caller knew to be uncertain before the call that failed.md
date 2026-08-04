---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  At least half of the failed calls came from a caller showing prior signs of
  doubt.
instrument: npx vitest run test/telemetry/preflight-uncertainty-census.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that callers know when they are uncertain. A validate-only twin helps only someone who thinks to use it, and the evidence points the other way: three identical rung refusals in one day suggests a caller who was confident and wrong, not one who was hesitating.

**Risk category: usability.**

**Design.** Take every failed call in the usage traces. For each, read the surrounding session record and judge whether the caller showed any sign of doubt beforehand — a hedge, a check, a question. Count how many failures came from a caller who would plausibly have chosen to validate first.

**Why it is small.** The traces and the transcripts both exist; this is reading them against each other.

**What it will not cover.** Judging doubt from a transcript is imprecise, and a caller who would validate reflexively before every risky call is not the same as one who felt uncertain. Both readings are worth recording separately.

A human runs this and records the result.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/telemetry/preflight-uncertainty-census.test.ts — The corpus this test asks about — every failed call, with what the caller did immediately before it — is already on disk in the captured usage and transcript records, so the count is a classifier over committed fixtures rather than anyone's afternoon; it fails today because neither the spec nor the classifier exists.

## What a green run does not settle

The command counts, over committed fixtures, how often a failing call was preceded by the caller showing it was unsure — a hedge in its own message, or a read issued before the write. That is the whole of what it answers.

It does not answer whether a validating call would have been *made*. A caller that was demonstrably uncertain and still committed to the real call is evidence against this solution, not for it, and the census cannot distinguish the two without the dry-run path existing to be declined. It also says nothing about desirability or viability: nobody outside this project has asked for a validate-before-commit call, and the census will not produce that evidence however it comes out.

One honest weakness in the bar. "Knew to be uncertain" is inferred from behaviour rather than observed directly, so the classifier's rule is a proxy chosen by whoever writes the spec. The rule must be committed in the spec file rather than tuned after seeing the count, or the number means nothing.

## Instrument Log
- 2026-08-04 **red** (exit 1) `npx vitest run test/telemetry/preflight-uncertainty-census.test.ts` — No test files found, exiting with code 1
- 2026-08-04 **green** (exit 0) `npx vitest run test/telemetry/preflight-uncertainty-census.test.ts` — Duration  249ms (transform 31ms, setup 0ms, collect 39ms, tests 4ms, environment 0ms, prepare 24ms)
