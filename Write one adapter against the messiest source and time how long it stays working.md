---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: 'Working within 4 hours, and at most 1 intervention in the following 30 days.'
instrument: npx vitest run test/adapters/messiest-source-replay.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that adapters are cheap enough to write and stable enough to keep, so that a per-source adapter is a reasonable ongoing commitment rather than a maintenance tax that grows with every source added.

**Risk category: feasibility.**

**Design.** Pick the least convenient source the operator actually holds experiment data in, write one read-only adapter for it, and record two numbers: hours to working, and days until it broke or drifted. Run it for a month and count interventions.

**Why it is small.** One adapter, not a framework. If the worst case is affordable the rest follow; if it is not, the approach is answered before any of them is written.

**What it will not cover.** A single source is a sample of one, and the operator writing the adapter knows both sides of it. A different source with an unstable API could be an order of magnitude worse, and this would not see it.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/adapters/messiest-source-replay.test.ts — Durability against a drifting source is testable without waiting for real time to pass by replaying the source's own historical snapshots in order and asserting the adapter parses every one; it fails today because no adapter for that source exists and no snapshot corpus is committed.

## What a green run does not settle

Replaying historical snapshots is a proxy for durability, not durability itself. Green means the adapter survives every drift the source has already shown; it cannot mean it will survive the next one, and the honest reading is "it would not have broken over the period we have on record".

The proxy has a specific blind spot worth naming: snapshots capture what the source *returned*, not changes to how it is reached — an auth change, a rate limit, a moved endpoint. Those are the failures most likely to break a pull adapter in practice and none of them appear in a replay corpus.

Nothing here bears on whether reading this source directly is worth doing. That the messiest source *can* be adapted says nothing about whether the records it yields change a single node in the tree, which is the question that decides whether any adapter should be written.

## Instrument Log
- 2026-08-07 **red** (exit 1) `npx vitest run test/adapters/messiest-source-replay.test.ts` — No test files found, exiting with code 1
