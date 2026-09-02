---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  At least 3 of 5 scopes are expressible without a clause that could be
  satisfied vacuously.
instrument: npx vitest run test/eval/gate-scope-expressibility.test.ts
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that a gate's intended coverage can be written down up front. That is easy for files and hard for behaviours, and a scope that cannot be expressed cannot be enforced.

**Risk category: feasibility.**

**Design.** Take five gates this project already has. For each, attempt to write its intended coverage in a form a program could check — which files, which cases, which behaviours must be exercised. Record which succeed cleanly, which need a vague clause, and which cannot be written at all. Note whether the vague ones could be satisfied by keeping the scope and hollowing out what happens inside it.

**Why it is small.** Five gates already exist. The exercise is writing, and failing to write is the result.

**What it will not cover.** Whether an author would keep the scope current as the gate's purpose evolves — which is where a written scope most plausibly rots.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/eval/gate-scope-expressibility.test.ts — The bar is countable — "At least 3 of 5 scopes are expressible without a clause that could be satisfied vacuously" — and the node is explicit that failing to write a scope is itself the result, which makes this a spec rather than an essay: the scope declarations either exist in a machine-checkable form for five of this project's existing gates, or they do not. The spec requires a declared scope per gate (which files, which cases, which behaviours must be exercised), asserts each is evaluable by the checker rather than free prose, and applies the vacuity test the node asks for — hollow out what happens inside the scope and confirm the declaration goes red, since a clause satisfiable by an empty body is precisely the failure being counted. Three of five must survive both. It fails today because no gate in the repository declares its intended coverage: gates assert outcomes and nothing records what they were meant to cover, so there is nothing to check for vacuity and the count starts at zero. What it does not settle is the rot the node names — whether an author keeps a written scope current as the gate's purpose evolves is a habit over months, and no single exit code observes it.

## Instrument Log
- 2026-08-07 **red** (exit 1) `npx vitest run test/eval/gate-scope-expressibility.test.ts` — No test files found, exiting with code 1
- 2026-09-02 **green** (exit 0) `npx vitest run test/eval/gate-scope-expressibility.test.ts` — Duration  241ms (transform 24ms, setup 0ms, collect 25ms, tests 4ms, environment 0ms, prepare 26ms) [spec 2ef65a85fdd4]
