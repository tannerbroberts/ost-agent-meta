---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: Week two's action rate is at least 70% of week one's.
instrument: npx vitest run test/loop/block-notification.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that notifications keep working. An operator notified about every wait will start ignoring them, at which point the mechanism is worse than nothing because it looks like it is working.

**Risk category: usability.**

**Design.** For two weeks, send a notification the moment any run blocks on the operator. Record, per notification, the time until they acted and whether they acted at all. Compare week one against week two.

**Why it is small.** The notification is a message; the measurement is two timestamps per event.

**What it will not cover.** Two weeks is short for habituation, which often takes longer to set in. A flat result across two weeks is weak evidence of durability, while a decline within two weeks would be strong evidence against.

A human runs this and records the result.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/loop/block-notification.test.ts — Asserts the notification fires at the moment the run blocks and carries both things the node says make it useful — the exact command that would unblock it and what is queued behind it. Red today because a run that hits an operator-only step records the block and tells nobody.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/loop/block-notification.test.ts` — No test files found, exiting with code 1
