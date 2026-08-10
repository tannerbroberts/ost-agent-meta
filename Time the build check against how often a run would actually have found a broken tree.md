---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  The check costs under 30 seconds, and at least 1 broken start appears per 50
  runs in the history.
instrument: npx vitest run test/loop/inherited-tree-build-check.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that the tax is worth the catch. A build on every run is a real cost paid mostly for nothing, and it comes too late to prevent anything — so the question is the base rate of arriving at a broken tree.

**Risk category: viability.**

**Design.** Two numbers. First, time the check at its cheapest useful form — a typecheck rather than a full build. Second, walk the commit history and count how many times a run started from a commit that did not build. Multiply the cost by the number of runs and compare against what those broken starts cost.

**Why it is small.** One timing and one history walk, both over material that exists.

**What it will not cover.** The cost of a broken start is estimated rather than measured, and the one instance on record cost an entire session's planning plus a human's attention — a sample of one, and an expensive one.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/loop/inherited-tree-build-check.test.ts — Asserts a run refuses to plan work on a tree that fails its own check, and bounds what that check costs; fails today because a run plans against whatever tree it inherits without checking it.

## Instrument Log
- 2026-08-07 **red** (exit 1) `npx vitest run test/loop/inherited-tree-build-check.test.ts` — No test files found, exiting with code 1
- 2026-08-10 **green** (exit 0) `npx vitest run test/loop/inherited-tree-build-check.test.ts` — Duration  2.02s (transform 21ms, setup 0ms, collect 25ms, tests 1.80s, environment 0ms, prepare 28ms)
