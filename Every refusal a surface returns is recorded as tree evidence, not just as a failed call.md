---
type: Solution
source: 'USAGE:2026-08-05'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A permission denial is distinguishable from a tool failing on its own terms]]

**The idea.** When a tool call is refused for lack of a grant, the refusal is written to the vault as an evidence record naming the tool, the surface, and the work it was about to do — so the shape of each surface accumulates instead of being rediscovered.

**Why this shape.** The usage channel already records that a call failed: on 2026-08-05 it caught `ost_read_repo` failing with "no product repos configured" out of 583 calls. But a *permission* denial is not the same event as a tool erroring on its own terms, and the corrections block prepended to each pass shows the current mechanism is a hand-maintained list of past refusals rather than a channel. Refusals are the one friction guaranteed to recur, because a grant does not change on its own.

**How it differs from its siblings.** Retrospective rather than preventive. It does not stop a degraded pass — the pass still runs degraded — but it is the only one of the three that makes the difference between surfaces visible over time, and it needs no operator to declare anything in advance.

**Where it fails.** It records what was *attempted*. A capability the agent never reached for, because it had already learned not to, leaves no trace — so the record drifts toward the tools the agent is most persistent about and away from the ones it has quietly given up on.

⚠️ Unvalidated. Agent-ideated.

## Definition of done

"Replay a denied call and a tool error and check they land as different records"

```
npx vitest run test/adapters/usage-denial-classification.test.ts
```

Named in plain text rather than linked: the test is already wikilinked by its parent assumption, and a title is linked exactly once in the vault.
