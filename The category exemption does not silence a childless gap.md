---
type: AssumptionTest
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
threshold: >-
  A fixture opportunity with exactly one sub-opportunity and zero solutions
  anywhere in its subtree is still reported as under-served; a fixture category
  with one sub-opportunity carrying three solutions is not.
instrument: npx vitest run test/ost/next-work-category-exemption.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**What it measures.** The false-negative rate of the cheapest rule in this branch, on the one shape that decides whether it is safe. Having a child is the exemption's entire evidence; the test asks whether that evidence survives the case where the child is empty too.

**Why it is red today.** No exemption exists — the current check reports both fixtures — so the second assertion fails immediately, and the first passes for the wrong reason. The file must assert both so the difference is visible.

**Honest limit on the instrument.** Written without repo sight; the path does not exist, so the first failure is a missing file rather than a failing assertion. See "My instruments are red because a file is absent, not because the behaviour is".

**What a green here does not settle.** Whether the exemption is preferable to rollup or to leaf redirection — that is a comparison across three candidates and this file only examines one. It also says nothing about how many real nodes in the live tree have the dangerous shape, which is a census, not a spec.

## Instrument Log
- 2026-08-07 **red** (exit 1) `npx vitest run test/ost/next-work-category-exemption.test.ts` — No test files found, exiting with code 1
- 2026-08-10 **green** (exit 0) `npx vitest run test/ost/next-work-category-exemption.test.ts` — Duration  2.39s (transform 116ms, setup 0ms, collect 176ms, tests 2.02s, environment 0ms, prepare 22ms)

## The census found zero childless gaps in the current population — 2026-08-09

**Not a recorded result.** Corroboration only, from the unattended sweep of 2026-08-09.

This assumption's falsifier is stated precisely: *"A node with one or more Opportunity children where neither it nor any descendant carries a solution — silenced by this rule and genuinely a gap."*

All 21 opportunities the sweep reported as under-served were checked for exactly that shape. **None matched.** Every one had a Solution somewhere beneath it, so on today's tree the exemption would silence 21 nodes and every one of those silences would be correct. Zero incorrect silences in the current population.

**Why that is weaker evidence than it looks, and the weakness is the point.** This measures the nodes the counter *already reports*, and a childless gap of the kind this assumption fears would be reported too — so the population was the right one to look in. But it is one tree, at one moment, maintained by one agent, and the shape the assumption fears is created by an ordinary event: a leaf need acquires a single sharper child before anyone ideates under either. That event has not happened to be caught here; nothing in this census says it is rare, only that it is currently absent.

The node this assumption names as the live example — "The same refusal is rediscovered every session, because nothing carries the lesson forward" — was read directly this pass. It carries three Solutions of its own *plus* one Opportunity child, so it is not a childless gap; the exemption would silence it, and the body above is right that the silence is correct in its case.

**What would actually settle it,** and this census does not: the same count taken on a second vault with a different author, or taken on this one after a deliberate leaf-split with no ideation, where the failing shape is constructed rather than waited for.

_Agent self-observation of this vault's structure. Grounds feasibility, not demand. No test run, no result recorded, rung unchanged._
