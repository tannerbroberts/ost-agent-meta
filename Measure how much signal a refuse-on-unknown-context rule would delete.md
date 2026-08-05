---
type: AssumptionTest
source: 'agent:ideation-2026-08-03'
created: '2026-08-03'
evidence: assertion
threshold: >-
  Fewer than 5 of the last 100 recorded steps would have been refused; and of
  those refused, none is a failure anyone later acted on.
instrument: npx vitest run test/telemetry/unknown-context-refusal-cost.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: viability** — specifically, whether the cure costs more than the disease. This solution deliberately throws information away: a failure with unknown context is still a signal that something broke, and refusing to record it loses that. The question is how often that happens.

**The test.** Take the last hundred recorded steps. Determine, for each, whether the recorder could have established its context. Count how many would have been refused. Then take that refused set and check the second condition: did anyone act on any of them later — a fix, an issue, a follow-up commit? A refused record that someone used is a signal this rule would have destroyed.

**Why there are two conditions.** A low count alone is not enough. If the five refused records happen to be the five that mattered, the rule is bad even at 5%. The second condition is what makes this a real test rather than a rate.

**Why the threshold is strict.** This is the cheapest of the three siblings and its whole claim is that it costs nothing real. A rate above 5% means it is not a cheap safety net, it is a policy change with consequences, and the middle version named in the solution body — record it but mark it `context-unknown` and exclude it from any count implying reproducibility — becomes the better candidate.

**A likely outcome worth pre-committing to:** if the count is very low, this is worth shipping *regardless* of what the other two siblings do, because it is nearly free and they do not cover the same failure.

Proposed, not run. Recording a result is a human's `ost-agent result`.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/telemetry/unknown-context-refusal-cost.test.ts — Both clauses of this node's threshold are computable over records already on disk — "Fewer than 5 of the last 100 recorded steps would have been refused; and of those refused, none is a failure anyone later acted on" — and the second clause is the one that makes it a test rather than a rate, which is exactly why it must be in the command and not left to a reader. The spec takes the last hundred entries from the health run record, determines for each whether the recorder could have established its context, counts the refusals against the fewer-than-5 bar, then traces each refused entry forward through git for a fix, an issue, or a follow-up commit that cites it, and fails if any refused record turns out to be one somebody used. It fails today because nothing decides whether a step's context is determinable: the recorder writes what it was given, there is no unknown-context predicate anywhere in the repository, and no code links a recorded failure to the later commit that addressed it. What it does not settle is whether the middle option the solution body names — record it but mark it `context-unknown` and exclude it from any count implying reproducibility — is the better candidate; this command prices refusal and says nothing about the alternative.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/telemetry/unknown-context-refusal-cost.test.ts` — No test files found, exiting with code 1
