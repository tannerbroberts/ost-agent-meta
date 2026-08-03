---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: Week two's action rate is at least 70% of week one's.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that notifications keep working. An operator notified about every wait will start ignoring them, at which point the mechanism is worse than nothing because it looks like it is working.

**Risk category: usability.**

**Design.** For two weeks, send a notification the moment any run blocks on the operator. Record, per notification, the time until they acted and whether they acted at all. Compare week one against week two.

**Why it is small.** The notification is a message; the measurement is two timestamps per event.

**What it will not cover.** Two weeks is short for habituation, which often takes longer to set in. A flat result across two weeks is weak evidence of durability, while a decline within two weeks would be strong evidence against.

A human runs this and records the result.
