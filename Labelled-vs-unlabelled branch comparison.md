---
type: AssumptionTest
status: unvalidated
source: 'agent:P4_assumptions'
created: '2026-07-24'
evidence: assertion
instrument: npx vitest run test/ost/evidence-class-on-every-node.test.ts
---
#AssumptionTest #unvalidated #usability #evidence/assertion

**Assumption under test (usability, with desirability implications):** Seeing an evidence class on a node changes what a reader is willing to act on, rather than becoming a badge they scroll past.

**Proposed test:** Show five people the same branch twice — once plain, once with evidence classes on every node. Ask each time: "which part of this would you commit a week of work to, and why?" Compare answers and reasons.

**Size:** an afternoon; needs only rendered mock-ups, no implementation.

**Pre-committed threshold:** ≥4 of 5 identify the weakest-evidence node in the labelled version AND at least 3 change their stated next action between versions. If the answers are identical, the labels cost writing effort and buy nothing.

**Decides:** whether per-node labelling is worth the friction it adds to every write, versus branch-level propagation.

Proposed by the agent — to be run by a human with real readers. No results recorded here.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 instrument: (none) → npx vitest run test/ost/evidence-class-on-every-node.test.ts — The test asks whether readers act differently on a labelled branch, which presumes the branch is fully labelled — and "required on every node" is not currently an invariant the tree checks, only a field the create tool happens to demand, so nodes written before the ladder or by any other path can carry none. This asserts the requirement: `ost_check` fails a vault containing any node without an evidence class, and the rollup's weakest-rung line is computed over every node rather than over the labelled subset, so an unlabelled node cannot silently improve the floor. Missing-spec red, not assertion red — this pass cannot read the repo, so the file is absent; a builder should write it against the real check rules so it goes red on an unlabelled node that today passes. It settles nothing about the test's actual threshold — 4 of 5 readers identifying the weakest node and 3 changing their stated next action — which needs five people and stays with a human.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/ost/evidence-class-on-every-node.test.ts` — No test files found, exiting with code 1
- 2026-08-17 **green** (exit 0) `npx vitest run test/ost/evidence-class-on-every-node.test.ts` — Duration  324ms (transform 94ms, setup 0ms, collect 137ms, tests 2ms, environment 0ms, prepare 31ms)
