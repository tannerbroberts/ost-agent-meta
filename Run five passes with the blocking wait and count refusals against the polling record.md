---
type: AssumptionTest
status: unvalidated
created: '2026-08-02'
evidence: assertion
threshold: >-
  Zero blocked-call refusals across the five passes, and wall-clock time no
  worse than the polling baseline.
---
#AssumptionTest #viability #unvalidated #evidence/assertion

**The assumption under test (viability):** that adopting the blocking wait actually removes the cost, rather than moving it. The transcript record gives an unusually good baseline — thirteen sessions of poll-and-retry, with counted refusals and timeouts — so the comparison is against real prior behaviour rather than an estimate.

**How it would run:** five passes that would normally poll a pending check, using the blocking wait instead. Count blocked-call refusals, timeouts, and wall clock. Compare against the same counts in the thirteen recorded sessions.

**The result that would be most useful:** finding that refusals go to zero while wall clock is unchanged. That would confirm what this candidate is honestly for — it fixes the shape of the waiting, not its cost — and would strengthen rather than weaken the case for the handoff design as the change that alters the economics.

Proposed by the agent; a human runs it and records the outcome.
