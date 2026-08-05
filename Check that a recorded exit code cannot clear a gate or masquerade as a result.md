---
type: AssumptionTest
created: '2026-08-05'
evidence: assertion
threshold: >-
  A recorded exit code writes only to the instrument log, never to Results,
  never changes status, and leaves the solution's gate BLOCKED.
instrument: npx vitest run test/runner/exit-code-observation.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**The assumption: an observation can be recorded without becoming a verdict.** This is the line the tree's entire discipline rests on. An exit code sitting next to a test looks enormously like a result, and if a green can clear a gate then compute has just granted itself the permit that promotion was reserved for.

**Risk category: feasibility, and the failure mode is a safety failure rather than a performance one.**

**Design.** Run the runner over an instrumented test and assert four things: it appends to the instrument log only; it does not write `## Results`; it does not change the node's status; and `ost_gate` for the parent solution still reports BLOCKED afterwards, whatever the exit code was. Assert the same for exit code 0 specifically, since that is the tempting case.

**Why it is small.** One test, one runner invocation, four assertions — and it is the cheapest possible check on the property that decides whether this candidate is safe to build at all.

**What it does NOT cover.** Whether the exit codes mean anything. The node's own stated failure is that a suite failing for environment reasons returns the same 1 as one failing because the behaviour is missing — a distinction this tree already carries as [[A test that failed because the machine was busy looks exactly like one that failed because I broke something]]. A perfectly-contained runner filling the vault with uninterpretable 1s would pass this test completely. Whether the observations are worth having is a human's read of the first batch.
