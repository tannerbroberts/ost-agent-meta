---
type: AssumptionTest
created: '2026-08-05'
evidence: assertion
threshold: >-
  Every construct the parser rejects appears in the published grammar, and the
  grammar is obtainable without submitting an artifact.
instrument: npx vitest run test/skill/published-grammar.test.ts
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**The assumption: the constraint can be stated in full ahead of time.** A published grammar that is incomplete is worse than none — a composer who reads it and then violates an unlisted rule has paid the reading cost and still learned by rejection.

**Risk category: feasibility.**

**Design.** Enumerate every construct the parser rejects and assert each appears in the published grammar. Assert the grammar is retrievable without submitting an artifact — the whole point is that obtaining it must not require being wrong first. Add a drift assertion so the grammar and the parser cannot diverge silently, since a stale grammar teaches a dialect the surface has moved off.

**Why it is small.** The rejection cases already exist in the parser; this is an enumeration and a comparison.

**What it does NOT cover.** Whether anyone reads it. The node concedes this is the weakest of its three siblings for exactly that reason: writing TypeScript into a JavaScript-only file is a habit rather than a knowledge gap, and habits do not consult references. A complete, accurate, drift-tested grammar that no composer opens changes nothing, and only watching composers would reveal that.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/skill/published-grammar.test.ts` — No test files found, exiting with code 1
- 2026-09-02 **green** (exit 0) `npx vitest run test/skill/published-grammar.test.ts` — Duration  278ms (transform 43ms, setup 0ms, collect 55ms, tests 12ms, environment 0ms, prepare 31ms) [spec 8ca6d3d36a75]
