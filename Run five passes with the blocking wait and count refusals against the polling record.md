---
type: AssumptionTest
status: unvalidated
created: '2026-08-02'
evidence: assertion
threshold: >-
  Zero blocked-call refusals across the five passes, and wall-clock time no
  worse than the polling baseline.
instrument: npx vitest run test/loop/blocking-wait-refusal-parity.test.ts
---
#AssumptionTest #viability #unvalidated #evidence/assertion

**The assumption under test (viability):** that adopting the blocking wait actually removes the cost, rather than moving it. The transcript record gives an unusually good baseline — thirteen sessions of poll-and-retry, with counted refusals and timeouts — so the comparison is against real prior behaviour rather than an estimate.

**How it would run:** five passes that would normally poll a pending check, using the blocking wait instead. Count blocked-call refusals, timeouts, and wall clock. Compare against the same counts in the thirteen recorded sessions.

**The result that would be most useful:** finding that refusals go to zero while wall clock is unchanged. That would confirm what this candidate is honestly for — it fixes the shape of the waiting, not its cost — and would strengthen rather than weaken the case for the handoff design as the change that alters the economics.

Proposed by the agent; a human runs it and records the outcome.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/loop/blocking-wait-refusal-parity.test.ts — Both halves of the threshold are mechanical — "zero blocked-call refusals across the five passes, and wall-clock time no worse than the polling baseline" — and the baseline is already on disk in the recorded poll-and-retry sessions, so no person is the measurement. The spec drives five passes through a blocking-wait primitive against a fixture that pends and then completes, asserts no invocation is refused with the harness's `Blocked:` message, and compares elapsed time against the counted timeouts and retries in the recorded sessions. It fails today because no blocking wait exists in the loop: the only waiting mechanism is poll-and-retry, which is what produced the refusals in the first place. This settles whether the refusals go away and whether the cost moves; it does not settle whether the handoff design is the better answer, which is the comparison the node says would actually change the economics.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/loop/blocking-wait-refusal-parity.test.ts` — No test files found, exiting with code 1
