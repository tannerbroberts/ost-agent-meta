---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Replay the last three tightenings and see whether the grandfathered backlog ever cleared]]

A rule records when it came into force. Nodes created before that moment are not violations; they are marked as predating the rule, and the check reports them in a separate class from things that broke it. A tightening produces a clean gate and a visible backlog, rather than a red gate the operator learns to ignore.

The distinction being preserved is between a tree that is wrong and a tree that is old. Those want different responses, and a check that collapses them into one number destroys the information needed to choose.

**Compared to the alternatives.** Costs nothing to the existing tree and keeps the gate meaningful the day a rule lands, which is the day it is most likely to be abandoned as unusable. It also lets the backlog sit forever with no pressure to clear it, and it makes every rule carry a date, so the check's output becomes a history lesson as much as a status.

**What would make this the wrong pick.** Grandfathering is how a codebase ends up with three generations of conventions, all live. If the point of tightening a rule was that the old nodes were genuinely a problem, exempting them by date answers the wrong complaint.

## Definition of done

[[Replay the last three tightenings and see whether the grandfathered backlog ever cleared]]

```
npx vitest run test/ost/grandfathered-backlog-replay.test.ts
```

Green means grandfathered nodes were actually brought into compliance after each of the last three tightenings rather than quietly accumulating — which is the question that decides whether forward-only is mercy or debt. A red run here is genuinely informative: it would say this candidate's core promise has already failed three times in this vault's own history.
