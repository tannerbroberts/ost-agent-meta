---
type: AssumptionTest
status: unvalidated
source: 'agent:P4_assumptions'
created: '2026-07-24'
evidence: assertion
instrument: npx vitest run test/loop/discovery-budget-reserved.test.ts
authorship: machine
---
#AssumptionTest #unvalidated #desirability #evidence/assertion

**Assumption under test (desirability):** Reserved discovery time produces evidence a human rates as useful, rather than guaranteeing effort that goes into low-signal busywork.

**Proposed test:** Reserve one pass a week for three weeks, unspendable by build work. After each, a human rates the output on one question: "did this change what I believe about the product, or what I plan to do next?" Yes or no, no partial credit.

**Size:** three weeks, using the schedule that already exists.

**Pre-committed threshold:** ≥2 of 3 passes rated yes. Below that the budget is protecting motion rather than progress, and the sibling that constrains *what* gets built deserves the compute instead.

**Decides:** whether guaranteeing discovery volume actually raises evidence quality — the assumption on which this whole sibling set turns.

Proposed by the agent — a human does the rating; the agent must not rate its own passes. No results recorded here.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 instrument: (none) → npx vitest run test/loop/discovery-budget-reserved.test.ts — A budget that build work can borrow from is not protected, and there is no reservation of any kind today — which is the opportunity "Building crowds out the search for better evidence" stated as a mechanism. This asserts the protection: a configured share of passes is reserved for discovery, a build-shaped pass is refused once the reserve is the only budget left, and the reserve does not roll over so an unused discovery pass is spent or lost rather than banked against future building. Missing-spec red, not assertion red: this pass holds no repo-read grant, so the file is absent; a builder should write it against the real loop scheduler so it goes red on a build pass that today consumes the reserve unopposed. It does not settle whether the reserved passes were USEFUL — rating them is a person's judgement and is what the test actually asks.

## Instrument Log
- 2026-08-07 **red** (exit 1) `npx vitest run test/loop/discovery-budget-reserved.test.ts` — npm notice
- 2026-08-30 **green** (exit 0) `npx vitest run test/loop/discovery-budget-reserved.test.ts` — Duration  9.88s (transform 22ms, setup 0ms, collect 16ms, tests 9.63s, environment 0ms, prepare 43ms)
