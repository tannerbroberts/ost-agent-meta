---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: 'At least 9 of 10 correct, 0 wrong, and 0 markers or broken links left behind.'
instrument: npx vitest run test/git/branch-isolation-merge.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that merging can be owned safely. If an unattended pass does it, the tree has swapped a collision it can detect for a resolution it cannot check — and the second is harder to notice, which is exactly how a conflict reached a commit before.

**Risk category: feasibility.**

**Design.** Construct ten realistic conflicts between two vault branches — same-titled nodes, competing appends to one parent's links, a status changed on both sides. Have an unattended pass resolve each. A person then grades every resolution as correct, lossy, or wrong, and separately checks whether any left a conflict marker or a broken wikilink behind.

**Why it is small.** Ten conflicts constructed from real nodes, one grading pass.

**What it will not cover.** Seeded conflicts are cleaner than real ones and were designed by someone who knows what makes them hard. Real collisions arrive with worse timing and less structure.

A human grades this and records the result.

## Issues
- 2026-08-05 2026-08-05 (unattended sweep) Left un-instrumented on purpose — this is a two-lane threshold and instrumenting it would answer the cheap clause while the expensive one stays open. "0 markers or broken links left behind" is mechanical: a spec can resolve ten seeded conflicts and assert that no conflict marker survives and every wikilink still resolves, and it would fail today because nothing in the repository resolves a vault merge at all. "At least 9 of 10 correct, 0 wrong" is not: correct-versus-lossy-versus-wrong is a person reading each resolution against what both sides meant, and the node says so plainly — "A human grades this and records the result." The two clauses are joined by "and" in one threshold field, so a single command would go green on the marker check — which nobody doubts is achievable — while the question the solution actually lives on, whether an unattended pass can be trusted to own a merge, went unasked. That is worse than no instrument, because a passing command under a solution reads as a cleared gate. For a human: split this into a hygiene test (instrumentable now: zero markers, zero broken links, over ten seeded conflicts) and a resolution-quality test (humans-required: 9 of 10 graded correct, 0 wrong). Neither write is available from this surface — creating the split node is out of the sweep's scope and `ost_flag_humans_required` is not granted here. Worth noting which way the risk points: the node's own framing is that an unattended merge swaps a collision the tree can detect for a resolution it cannot check, so the clause that resists automation is the one that matters, and it is the one that would have been left behind.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/git/branch-isolation-merge.test.ts — Asserts the isolation claim and the conflict shape the node predicts: two passes never share a working tree, sections appended to different nodes merge without conflict, and the genuine collisions — two nodes created with the same title, two edits to one parent's link list — surface as conflicts rather than resolving silently. Red today because passes write to one working tree and nothing branches per agent.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/git/branch-isolation-merge.test.ts` — No test files found, exiting with code 1
