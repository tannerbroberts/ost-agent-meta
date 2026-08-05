---
type: AssumptionTest
status: unvalidated
source: 'agent-ideated:2026-08-02-maintenance-pass-3'
created: '2026-08-02'
evidence: assertion
threshold: >-
  At least 2 of the current top 5 priority positions change, or an item
  enters/leaves the top 5; 1 or 0 changes kills the candidate.
instrument: npx vitest run test/product/manifest-ranking-shift.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**The assumption under test (desirability / value):** that a declared resource picture actually changes which work comes first. If the ranking is identical with and without it, the manifest is documentation, not a planner input, and should not be built.

**The test:** fill the manifest by hand for this vault from facts already recorded in it — zero human hours, no willingness to cold-contact strangers, no publish credential reachable from the container, a token budget with a reset schedule, no capital. Re-derive the top five items of the current priority order under those declared constraints, without looking at the existing order while deriving. Then diff the two lists.

**Pre-committed before running, so this can come out a failure:** two of the current top five must change position, or an item must enter or leave the top five. One change or none kills the candidate — it would mean the planner was already conditioning on these facts implicitly and the manifest buys nothing.

**What it deliberately does not cover:** whether an operator who is *not* the founder would fill the manifest at all, and whether the answers stay true. Those are the questions [[Expiring resource questions asked at a fixed cadence]] carries.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/product/manifest-ranking-shift.test.ts — Both halves are deterministic — rank the tree with the manifest absent, rank it again with a hand-filled manifest fixture, and diff the top five — so the count needs no judgement once the fixture is committed; it fails today because the manifest, the citation requirement and the spec are all unwritten.

## What a green run does not settle

The command shows only that a declared manifest *changes the ranking* — that the planner's output is sensitive to resources it was previously guessing at. That is the feasibility question, and it is the cheap one.

It does not show the new ranking is better. A manifest that reshuffles the top five proves the input matters, not that the output improved, and a spec has no way to judge which of two orderings a human would rather act on. That comparison needs a person who knows the work.

It also does not settle the cost that would actually sink this: somebody has to keep the manifest true. The fixture is hand-filled once, by definition, so nothing in this test speaks to whether an operator would maintain one — and a stale manifest the planner is *required* to cite is worse than no manifest, because it launders a guess into a citation.

## Instrument Log
- 2026-08-04 **red** (exit 1) `npx vitest run test/product/manifest-ranking-shift.test.ts` — No test files found, exiting with code 1
- 2026-08-05 **green** (exit 0) `npx vitest run test/product/manifest-ranking-shift.test.ts` — Duration  325ms (transform 69ms, setup 0ms, collect 119ms, tests 10ms, environment 0ms, prepare 24ms)
