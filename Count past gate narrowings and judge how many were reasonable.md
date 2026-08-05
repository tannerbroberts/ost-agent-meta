---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: Fewer than 2 narrowings per month on average.
instrument: npx vitest run test/security/gate-coverage-human-only.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that narrowings are rare enough to route through a person. If they are frequent and mostly reasonable, a human bottleneck creates pressure to set gates loosely from the start so they never need narrowing — a worse outcome reached by a respectable route.

**Risk category: viability.**

**Design.** Search the commit history for every change that reduced what a gate covered — an added exclusion, a skipped case, a relaxed threshold. Count them and date them. For each, a person judges whether it was reasonable. Compute the rate per month and the share judged reasonable.

**Why it is small.** The history exists; this is reading and judging it.

**What it will not cover.** The judge is the person who made most of these changes, which biases toward reasonable. The rate is the more reliable half of the finding.

A human runs this and records the result.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/security/gate-coverage-human-only.test.ts — Counting past narrowings presumes a narrowing is a distinguishable, attributable event, and today it is not — nothing separates a change to what a gate covers from any other write. This asserts both halves of the solution: a call on the agent surface that would reduce a gate's coverage is refused rather than recorded, and a human's coverage change lands as its own commit touching only the gate definition, so it can be counted from git alone rather than reconstructed. Missing-spec red, not assertion red: the pass cannot read the repo, so the file is absent; a builder should write it against the real gate definitions so it goes red on an agent-surface narrowing that today succeeds. It does not settle whether past narrowings were REASONABLE — that judgement is a person's, and it is the half the test actually names.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/security/gate-coverage-human-only.test.ts` — No test files found, exiting with code 1
