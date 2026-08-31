---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: The two labellings agree on at least 85% of items.
instrument: npx vitest run test/loop/stop-condition.test.ts
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that "actionable by this actor right now" is decidable in a way two readers would agree on. If it is not, the predicate becomes a place to hide the same ambiguity, and a loop reading it will be exactly as confused as before while sounding more certain.

**Risk category: feasibility.**

**Design.** Take one full sweep from this vault — every outstanding item across every bucket — and have two people independently label each as actionable by an unattended pass or not, working from the ruleset alone and without conferring. Compare, and read every disagreement to see whether it is a rule that needs stating or a genuine judgement call.

**Why it is small.** One sweep, two readers, an afternoon. The disagreements are the output, and they are directly usable as the specification for the predicate.

**What it will not cover.** Two readers who both know this vault well may agree for reasons a mechanical rule could not reproduce. High agreement is necessary for the predicate to be worth building and does not establish it can be written.

A human runs this and records the result.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/loop/stop-condition.test.ts — Two people labelling a sweep are checking a judgement the loop has to make on its own every time it wakes, and the loop currently has no published rule to check against — which is how a pass ends up either idling or inventing work. This asserts the rule exists and is evaluable: the loop publishes a stop condition as data rather than prose, a sweep with nothing actionable makes it evaluate true and the pass idles without writing, and a pass that writes while the condition holds fails. Missing-spec red, not assertion red — no stop condition is published anywhere, so the command fails on a missing file; a builder should write it against the real loop entry so it goes red on a pass that manufactures work against an empty sweep. It does not settle whether the condition AGREES with people — that is the two-labeller comparison, and it stays with humans.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/loop/stop-condition.test.ts` — No test files found, exiting with code 1
- 2026-08-31 **green** (exit 0) `npx vitest run test/loop/stop-condition.test.ts` — ✓ 3 — a pass that writes while the condition holds fails > authoring structure against an empty sweep seals unhealthy 1467ms
