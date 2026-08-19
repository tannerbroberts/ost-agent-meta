---
type: AssumptionTest
status: unvalidated
created: '2026-08-02'
evidence: assertion
threshold: >-
  Agreement on at least eight of ten, with no case where a session that
  abandoned its goal was scored as a clean recovery.
instrument: npx vitest run test/adapters/friction-recovery-rule.test.ts
---
#AssumptionTest #usability #unvalidated #evidence/assertion

**The assumption under test (usability):** that "did the session recover" is a good stand-in for what a human means by friction. The rule judges cost rather than error type, which is closer to the real definition — but it has to infer recovery from what follows in the transcript, and that inference is where it can go wrong.

**How it would run:** a human rates ten records as typo or friction without seeing the rule's answer, then the two are compared.

**The failure mode worth watching for:** a session that quietly gave up on something reads as a clean recovery. Any disagreement of that shape matters more than the headline agreement rate, because it is the same blind spot the tree already names under "The friction that matters leaves no error behind" — and it would mean this candidate needs pairing with something that can see silent abandonment rather than being adopted alone.

An hour of one person's time. Proposed by the agent; a human runs it and records the outcome.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/adapters/friction-recovery-rule.test.ts — Asserts the rule judges by what happened next rather than by the error itself: an error the session recovered from within a turn or two collapses into a counted summary line, while one that changed the session's direction, cost several attempts, or ended the work gets its own record. Red today because the harvester emits every tool_error as a flat event with no recovery classification at all — which is why 24 sessions produced 82 undifferentiated items.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/adapters/friction-recovery-rule.test.ts` — No test files found, exiting with code 1
- 2026-08-19 **green** (exit 0) `npx vitest run test/adapters/friction-recovery-rule.test.ts` — Duration  211ms (transform 21ms, setup 0ms, collect 20ms, tests 3ms, environment 0ms, prepare 30ms)
