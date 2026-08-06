---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Enough refusal classes are safe to absorb that removing the occasion is worth doing]]

For the refusal classes that recur most, stop correcting the caller and remove the occasion for the correction. If a blocking sleep-then-poll is always wrong and there is always a right way to wait, the surface can accept the wrong form and do the right thing, or offer the right thing so prominently that the wrong form is not reached for. A lesson nobody has to learn cannot be forgotten.

The candidates are visible directly in the friction record: eleven sessions blocked on the same wait idiom, five identical shell-quoting failures in a single session, two workflow scripts rejected for the same TypeScript-in-JavaScript reason. Each is a fixed rule the caller keeps failing to internalise, which is usually a sign the rule is in the wrong place.

**Compared to the alternatives.** The only option that eliminates the problem rather than routing around it, and the only one that costs nothing at run time. It is also the least general: it works one refusal class at a time, needs design judgement for each, and cannot touch refusals that exist for good reasons and must keep existing. A corrections file and a repeat detector are both general and both weaker.

**What would make this the wrong pick.** Some refusals are load-bearing safety, and accommodating the wrong form is how a guardrail becomes decorative. Which classes are safe to absorb is a human's call, not a pass's.

## History
- 2026-08-05 unlinked "Sort the top refusal classes into safe-to-absorb and load-bearing, and count each" — moved under "Enough refusal classes are safe to absorb that removing the occasion is worth doing" — the belief this test measures now has a node of its own

## Definition of done

"Sort the top refusal classes into safe-to-absorb and load-bearing, and count each"

```
npx vitest run test/mcp/refusal-absorption-census.test.ts
```

Red today because the census does not exist, not merely because the file does not: there is no ranked tally of refusal classes anywhere in the repository, so the spec has nothing to import.

The bar is the test's own — at least 4 of the top 10 classes judged safe to absorb, covering 30% or more of all refusals fired. Note which half of that pair is doing the work: four classes that are each rare would clear the count and fail the coverage, and absorbing them would change nothing an operator notices.

Green here proves a share of refusals is absorbable. It does not prove absorbing them is safe — the load-bearing half of the sort is a judgement about what a guardrail defends, and a census that gets that judgement wrong produces a confident number in favour of dismantling a guard. A human should read the load-bearing column before anything is built from the safe column.
