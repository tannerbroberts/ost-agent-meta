---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  Fewer than 10 of the 82 re-reads surfaced a change the caller could not have
  predicted.
instrument: npx vitest run test/mcp/sweep-version-and-delta.test.ts
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that the re-reads were not doing real work. Trading correctness for a cheaper trace is the wrong direction if they were, and nothing so far establishes that they were not.

**Risk category: viability.** This is the question that should be answered before any of the three options here is built.

**Design.** Take the day with 82 sweep calls. For each, compare what it returned against what the previous one returned. Count the re-reads that surfaced something new, and among those, how many were changes the caller itself had just caused as against changes it could not have predicted.

**Why it is small.** The traces record every call, and the tree's history records what changed between them.

**What it will not cover.** A re-read that returned nothing new still bought certainty, and certainty has value this cannot price. The count of genuinely unpredictable changes is the more decisive half.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/mcp/sweep-version-and-delta.test.ts — Judging whether a re-read caught anything new requires the sweep to be able to say whether anything changed, and today it cannot — it returns the same untagged payload every time, which is why a caller re-asks. This asserts the contract: the sweep carries a version, a re-read against an unchanged tree returns that same version with an empty delta, and a re-read after any write reports which buckets moved and by how much. Missing-spec red, not assertion red — no version or delta exists on the sweep, so the command fails on a missing file; a builder should write it against the real `ost_next_work` response so it goes red on the absent version field. It does not settle the test's question, which asks a reader to judge past re-reads for whether they were informative — that is a person's judgement over a historical trace.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/mcp/sweep-version-and-delta.test.ts` — No test files found, exiting with code 1
- 2026-08-28 **green** (exit 0) `npx vitest run test/mcp/sweep-version-and-delta.test.ts` — Duration  13.25s (transform 1.10s, setup 0ms, collect 1.67s, tests 9.94s, environment 0ms, prepare 182ms)
