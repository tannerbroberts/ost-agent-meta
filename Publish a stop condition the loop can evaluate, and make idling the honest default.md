---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Whether an item is actionable is decidable mechanically, not case by case]]

The tree gains an explicit, computable answer to "is there anything worth doing right now?" — not a count of open items, but a predicate over them: work that is both outstanding and actionable by whoever is asking. A loop that evaluates it and gets false stops, reports that it stopped because there was nothing it could do, and costs nothing until something changes.

The distinction that makes this work is between outstanding and actionable. The current sweep reports plenty of outstanding items that no unattended pass may touch — tests only a human may run, evidence that cannot be mapped without inventing a need. Counting those as work is what creates the pressure to invent.

**Compared to the alternatives.** This is the cheapest of the three and the only one that requires no new infrastructure — the predicate is a function over state the sweep already computes. It is also the weakest, because it tells the loop when to stop and nothing about when to start again; pairing it with a wake signal is the obvious next move but is a separate solution.

**What would make this the wrong pick.** If "actionable" turns out not to be mechanically decidable — if it needs a judgement call per item — then the predicate becomes a place to hide the same ambiguity, and a loop reading it will be exactly as confused as before with more confidence.

## Definition of done

[[Have two people independently label a full sweep's items as actionable or not, and compare]]

```
npx vitest run test/loop/stop-condition.test.ts
```

Green means: the rule exists as data rather than prose, an empty sweep makes it evaluate true and the pass idles without writing, and a pass that writes while the condition holds fails. That last assertion is what makes idling the *honest* default rather than the polite one. Green does **not** mean the condition agrees with people; the two-labeller comparison stays with humans.

## History
- 2026-08-05 unlinked [[Have two people independently label a full sweep's items as actionable or not, and compare]] — moved under [[Whether an item is actionable is decidable mechanically, not case by case]] — the belief this test measures now has a node of its own
