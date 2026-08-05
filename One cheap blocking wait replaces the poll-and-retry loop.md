---
type: Solution
status: unvalidated
created: '2026-08-02'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A blocking wait removes the refusals without costing wall-clock time]]

Keep the pass running, but make waiting a single call that blocks until the condition holds, instead of a sequence of asks separated by sleeps. The environment already refuses the sleep-then-check shape and already names the affordance that does this; the loop simply is not reaching for it.

**Compared with the alternatives:** by far the cheapest to adopt — no new infrastructure, no state between passes, and it removes the single most repeated friction event in the whole transcript record in one change. Its limit is that the pass is still occupied while it waits, so a two-hour check still costs a two-hour session; it improves the shape of the waiting without reducing what the waiting costs. It is best read as the immediate fix, with the handoff design as the one that actually changes the economics.

Unvalidated, agent-ideated: a candidate for comparison, not a recommendation.

## Definition of done

[[Run five passes with the blocking wait and count refusals against the polling record]]

```
npx vitest run test/loop/blocking-wait-refusal-parity.test.ts
```

Red today: no blocking wait exists in the loop, so every wait is still poll-and-retry. Green when five passes complete through the blocking primitive with zero `Blocked:` refusals and wall clock no worse than the recorded polling baseline.

**The baseline just got much better than an estimate.** The corroboration appended to [[My loop spends its time waiting for a check it cannot subscribe to]] on 2026-08-04 prices this candidate directly: one session re-issued the same 600-second full-suite command four times, three of them byte-identical, purely to learn whether the run it had already started had finished. And [[The same refusal is rediscovered every session, because nothing carries the lesson forward]] now records eight sessions across five days reaching for `sleep` and being refused. So the "polling record" this test compares against is thirteen-plus real sessions with counted refusals, not a construction.

**What this does not settle.** It measures whether the refusals stop and whether the cost moves. It does not measure whether waiting is the right shape at all — the node's own argument is that this fixes the shape of the waiting rather than its cost, and that the handoff design is the change that alters the economics. A green here leaves that comparison exactly where it was.

## History
- 2026-08-05 unlinked [[Run five passes with the blocking wait and count refusals against the polling record]] — moved under [[A blocking wait removes the refusals without costing wall-clock time]] — the belief this test measures now has a node of its own
