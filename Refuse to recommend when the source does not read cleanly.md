---
type: Solution
source: 'agent-ideation:2026-07-26-tenth-pass'
created: '2026-07-26'
evidence: assertion
---
#Solution #evidence/assertion
[[Count how many of this vault's recommendations would go silent under a refuse-when-unclear rule]]

**The idea.** When the agent cannot read a source into exactly one answer, it produces no recommendation at all — it reports the ambiguity and names what a human would have to settle. Silence in place of a confident half-reading.

**Contrast with its siblings.** Showing the fuller quote trusts the reader to catch the problem; this one refuses to put the problem in front of them in an actionable shape. It is the same fail-closed move the lane vocabulary already makes (`unclassified` is never `safe to automate`), applied to advice rather than to permission.

**Why it might be the right one.** The failure being defended against is *a reader who stops checking because a quote is present*. A solution that relies on that same reader reading more carefully is defending against the failure with the thing that failed.

**Where it fails, and this is the real cost.** Recommendations are the product's actual output. A rule that suppresses them whenever a source is qualified could suppress most of them — the vault's own writing is full of *mostly, except, for the census but not the fixing* — leaving an operator with a tool that mostly declines to help. **This wants a count before it wants an implementation:** how many of this vault's 83 assumption tests would go silent under it.

⚠️ Unvalidated. Agent-ideated.

## Definition of done

[[Count how many of this vault's recommendations would go silent under a refuse-when-unclear rule]]

```
npx vitest run test/knowledge/refuse-when-unclear-suppression.test.ts
```

Red today because the rule does not exist and neither does the counter: nothing in the repository decides that a source does not read cleanly, so there is nothing to suppress and no denominator to divide by. Green means at least 70% of current recommendations still render, counted per surface and per vault. Below 50% on either vault kills this solution rather than tuning it — a rule that silences half the output is a different product decision and has to be argued as one.

Per-surface, not pooled. A rule that leaves hygiene findings intact while silencing every caution hint would pass on a combined number and fail the question being asked.

What it does not settle, and it is the half that matters most: the count is a cost measurement, not a benefit one. A rule could silence 5% and silence exactly the 5% that were correct and load-bearing, and this command cannot tell that apart from silencing 5% of noise.
