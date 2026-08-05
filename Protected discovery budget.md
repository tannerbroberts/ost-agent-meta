---
type: Solution
status: unvalidated
source: 'agent:P3_ideate'
created: '2026-07-24'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Discovery done because the budget exists is as useful as discovery done because someone chose it]]

Reserve a fixed share of compute and schedule for discovery that build work cannot spend, on a recurring cadence. Discovery happens because the budget exists, not because someone chose it over shipping.

**How it differs from its siblings:** guarantees an *amount* of discovery rather than a division of labour or a precondition for building. Cheapest of the three, and the only one that keeps running when there is nothing to gate and no builder yet.

**Trade-off:** a protected budget guarantees effort, not value — it can be spent on low-signal busywork and still look satisfied.

**Riskiest assumptions to test:** that reserved discovery time produces evidence a human rates as useful (desirability); that the reservation survives a deadline (viability).

Status: agent-originated candidate. Unvalidated.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked "Three reserved discovery passes rated for usefulness" — moved under "Discovery done because the budget exists is as useful as discovery done because someone chose it" — the belief this test measures now has a node of its own

## Definition of done

"Three reserved discovery passes rated for usefulness"

```
npx vitest run test/loop/discovery-budget-reserved.test.ts
```

Green means: the reserve is actually protected — a configured share of passes is held for discovery, a build-shaped pass is refused when the reserve is all that remains, and unused discovery passes do not roll over into building. A budget build work can borrow from is not a protection. Green does **not** rate the passes; whether the reserved ones were useful is the human judgement the test asks for.
