---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: The accumulated sweep matches a fresh read exactly after at least 100 writes.
instrument: npx vitest run test/mcp/sweep-delta-consistency.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that every write can compute its consequences correctly. A write that gets them wrong leaves the caller confidently out of step with the tree — a failure with no symptom until something surprising happens.

**Risk category: feasibility.**

**Design.** Over one full pass, have each write return its delta and maintain a locally accumulated sweep. Do not consult it. At the end, produce a fresh sweep from the tree and compare the two field by field. Every divergence is a write whose delta computation is wrong.

**Why it is small.** One pass, and this pass alone made over two hundred writes — a large sample from a single run.

**What it will not cover.** It assumes a single writer, which is exactly the condition under which the approach is correct. The interesting failure — drift when a second agent is writing — is invisible to this and needs a concurrent arm.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/mcp/sweep-delta-consistency.test.ts — The threshold — the accumulated sweep matches a fresh read exactly after at least 100 writes — is settled entirely inside the process: the spec drives more than a hundred writes against a fixture vault, accumulates only the deltas each write returns without ever consulting the tree, then produces a fresh sweep and asserts the two agree field by field. It fails today because writes return no delta at all.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/mcp/sweep-delta-consistency.test.ts` — No test files found, exiting with code 1
- 2026-08-18 **green** (exit 0) `npx vitest run test/mcp/sweep-delta-consistency.test.ts` — Duration  82.36s (transform 1.04s, setup 0ms, collect 1.83s, tests 79.24s, environment 0ms, prepare 119ms)
