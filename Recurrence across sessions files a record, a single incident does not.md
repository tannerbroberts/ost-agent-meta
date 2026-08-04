---
type: Solution
status: unvalidated
created: '2026-08-02'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Replay the same 29 records through the recurrence rule and count what files]]

Make repetition the filing criterion. A one-off error is counted and held; the same error shape appearing across several distinct sessions is what creates an evidence record, and the record carries the count and the span rather than a single instance.

**Compared with the alternatives:** this is the candidate that best matches what the channel actually taught this pass — the individually worthless `== not found` becomes valuable precisely when it appears in ten sessions, and one blocked sleep is noise while thirteen is a design problem. It keeps the pattern the surface filter would throw away. Its costs are a delay before anything files, a need to decide when two errors count as the same shape, and a blind spot for the rare failure that matters on its first occurrence.

Unvalidated, agent-ideated: a candidate for comparison, not a recommendation.

## Definition of done

[[Replay the same 29 records through the recurrence rule and count what files]]

```
npx vitest run test/adapters/recurrence-rule-filing.test.ts
```

Green means the rule, replayed over the same 29 harvested records the surface rule was judged on, files five or fewer records in total, and both known patterns — the repeated refusal and the repeated poll — surface as single records carrying their count and span. It is red today because no recurrence rule exists.

**The grouping clause is the hard half, not the count.** Ten sessions saying `== not found` are obviously the same shape and any rule will collapse them. The thirteen blocked sleep-then-poll calls differ in their sleep durations and their target commands, and a rule that files those as thirteen records has not shown that repetition is mechanically detectable — it has shown that identical strings are. Asserting the count alone would go green on a rule that simply deduplicates.

**Why the same 29 records.** The candidate this competes with was scored on that corpus, so identical material is what makes the comparison mean anything. What decides between them is not the raw hit rate but whether this rule keeps the patterns the other discards while still filing few enough records that a pass can read them all.

**What green does NOT settle.** Repetition is a proxy for significance, and the proxy is the assumption. A failure that happened once and mattered enormously is filed by neither rule, and nothing in this command would show it.
