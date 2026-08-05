---
type: AssumptionTest
status: unvalidated
source: 'agent:P4_assumptions'
created: '2026-07-24'
evidence: assertion
instrument: npx vitest run test/loop/attempt-ledger-repeat-rate.test.ts
---
#AssumptionTest #unvalidated #feasibility #evidence/assertion

**Assumption under test (feasibility):** Consulting a record of what was already tried actually changes what gets proposed — rather than being written, never read, and quietly abandoned.

**Proposed test:** Seed a ledger with a handful of genuine dead ends. Run ideation twice on the same opportunity: once with the ledger available, once without. A human compares the two sets for repeats of known dead ends and for genuinely new directions.

**Size:** two ideation runs on one opportunity.

**Pre-committed threshold:** the ledger run repeats at least one fewer known dead end AND produces ≥1 direction the other run missed. No difference means the ledger is documentation, not a mechanism, and shouldn't be maintained.

**Watch for the failure mode:** if the ledger run is *narrower* rather than better, the ledger is freezing exploration — record that outcome too, it is the more important finding.

Proposed by the agent — a human compares the two sets. No results recorded here.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-04 instrument: (none) → npx vitest run test/loop/attempt-ledger-repeat-rate.test.ts — The half of the pairing that decides whether the ledger works is countable rather than judged — run ideation twice over the same fixture opportunity, once with the ledger of prior attempts and once without, and assert the ledger run proposes materially fewer solutions that duplicate what the ledger already records; it fails today because no attempt ledger exists.

## What a green run does not settle

Fewer repeats is the effect the ledger is meant to have, and it is also the effect a ledger could achieve by simply making ideation more timid. The count cannot tell those apart. A run that proposes three duplicates and four genuinely new solutions scores worse than one that proposes two duplicates and nothing else, which is the wrong ranking — so this bar needs reading alongside the absolute count of novel solutions, not on its own.

"Duplicate" is also a judgement rendered as a rule. Whatever similarity test the spec commits to will call some near-misses duplicates and let some restatements through, and the number moves with that choice. The rule must be committed before the run rather than tuned to produce a satisfying gap.

Nothing here shows the ledger is worth its cost — every pass pays to write and read it, and a solution that removes a handful of duplicates per opportunity may not repay that.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/loop/attempt-ledger-repeat-rate.test.ts` — No test files found, exiting with code 1
