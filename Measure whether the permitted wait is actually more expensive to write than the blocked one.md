---
type: AssumptionTest
created: '2026-08-05'
evidence: assertion
threshold: >-
  For each of the three observed waiting cases, the permitted form is no longer
  to express than the blocked form it replaces.
instrument: npx vitest run test/loop/wait-primitive-affordance.test.ts
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**The assumption underneath this candidate is a premise, and it has never been checked: that the reflex is driven by expression cost.** The node asserts `sleep 45 && gh pr checks 17` keeps getting written because it is the shortest way to say "wait for this". If the permitted form is in fact just as short today, then expression cost is not what is driving the repeat, and this entire candidate is aimed at the wrong cause.

**Risk category: feasibility — and it is a cheap disconfirmer, which is why it is worth running before the expensive build.**

**Design.** Take the three waiting cases visible in the evidence: poll a CI check, wait on a task that was started, wait for a condition to become true. For each, express it in the blocked form and in the permitted form, and compare. If the permitted form is already no longer, the premise is refuted and the node should be reconsidered rather than built.

**Why it is small.** Three expressions, no execution, and it can kill the idea before anyone designs a primitive.

**What it does NOT cover.** Whether a cheaper permitted form actually changes behaviour. The node concedes the alternative explanation directly — if the reflex is habit or training rather than economy, a cheaper option sitting right there will be ignored too — and only watching sessions after the change would settle that. This test can refute the premise; it cannot confirm the mechanism.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/loop/wait-primitive-affordance.test.ts` — No test files found, exiting with code 1
- 2026-08-28 **green** (exit 0) `npx vitest run test/loop/wait-primitive-affordance.test.ts` — Duration  3.94s (transform 70ms, setup 0ms, collect 77ms, tests 3.50s, environment 0ms, prepare 73ms)
