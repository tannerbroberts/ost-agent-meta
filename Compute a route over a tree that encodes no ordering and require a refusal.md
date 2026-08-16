---
type: AssumptionTest
source: 'agent-ideation:2026-08-09-unattended-sweep'
created: '2026-08-10'
evidence: assertion
threshold: >-
  Across the fixture branches, every computed route is either a correctly
  ordered chain or an explicit refusal naming the missing ordering. Zero
  arbitrary orderings emitted as confident routes. One emitted arbitrary
  ordering fails the test.
instrument: npx vitest run test/ost/route-from-edges.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility.**

**What this measures.** Not whether a chain can be produced — one always can — but whether the route computation can tell a tree that encodes an ordering from one that does not, and decline in the second case rather than drawing a confident line through unrelated work.

**The assertion the spec makes,** stated here so the command is a designed test rather than a reserved filename. Using the existing fixture helper at `test/ost/fixture-vault.ts`, build two vaults:

1. One whose opportunity sub-tree carries only nesting edges — subset relationships and sibling alternatives, which is what the grammar in `src/ost/node.ts` actually records. Ask for a route from a leaf to the root. The spec asserts the computation **refuses**, and that the refusal names what is missing — that these edges encode containment, not sequence.
2. One where an ordering is genuinely recoverable. Ask for the same route. The spec asserts an ordered chain comes back, and that its order is the recoverable one rather than file order, alphabetical order, or creation order.

The second case is what stops the first from being satisfied by a function that refuses everything.

**Why it is red today, and which kind of red.** It is a `no-spec` red, and that is stated plainly rather than left to be discovered. `test/ost/route-from-edges.test.ts` does not exist; `src/ost/` holds no route or path module, verified by listing it this pass. So the command fails on the missing file, which is the weaker of the two reds the ruleset distinguishes and grants no build permit on its own. It is filed this way because an unattended discovery pass has read-only repo sight: it can name the module that must change and state the assertion the spec must make, and it cannot leave the spec file behind. Turning this into a failing-assertion red is a builder's first act on this node, and it is small — the assertion is written above.

**Why it is small.** Two fixture vaults and one function under test. No new dependency, and the fixture helper already exists.

**What this does NOT settle, stated so a green is not over-read.** A pass here proves only that a route can be computed honestly from existing edges and that the computation knows when it cannot. It says nothing about whether seeing a route changes which work a builder picks up first — that is the sibling assumption on this solution, it names a person as the measurement, and no exit code observes one. It also says nothing about whether the routes produced are *useful* to a reader, only that they are not fabricated. A solution that passes this and fails the behavioural half is a correct feature nobody needed.

⚠️ Unvalidated. Agent-ideated; no test was run and no result is recorded.

## Instrument Log
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/ost/route-from-edges.test.ts` — test/ost/route-from-edges.test.ts does not exist — no spec was collected, so nothing was measured
