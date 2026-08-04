---
type: Solution
status: unvalidated
created: '2026-08-02'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Replay all 29 records through the surface rule and see what it keeps]]

Scope the filter by what the failing call was against. An error from the product's own tools becomes an evidence record; an error from a shell, an editor, or a script runner becomes a number in a periodic tally. Nothing is discarded — the tally is still there to be read — but only the first kind arrives claiming a pass's attention.

**Compared with the alternatives:** the cleanest rule to state and the cheapest to implement, since the tool name is already recorded on every event. It is also the bluntest: it would have discarded the observation that the same refusal recurs across seven sessions, which came from shell errors and is one of the more useful things this channel has produced. It optimises for precision and pays for it in exactly the place where the noise turned out to carry a pattern.

Unvalidated, agent-ideated: a candidate for comparison, not a recommendation.

## Definition of done

[[Replay all 29 records through the surface rule and see what it keeps]]

```
npx vitest run test/telemetry/friction-surface-rule.test.ts
```

Green means the rule keeps the records that touch this product's own surface and counts the rest rather than discarding them. The recorded material is a fair test of it: a great deal of the harvested friction is shell quoting and blocked polling in the harness, not in this product. It does not settle whether the counted-not-filed material was safe to demote, which is exactly what a rule like this risks getting wrong.
