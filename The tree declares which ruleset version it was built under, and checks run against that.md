---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Supporting two live ruleset versions costs few enough conditionals to stay maintainable]]

A vault records the ruleset version it is on. Checks evaluate against that version, so a tightening published today does not retroactively fail a tree that has not adopted it. Adopting is an explicit act: the operator moves the version, sees exactly what newly fails, and does that work when they choose to.

Control is the point. The operator decides when to take a tightening, in the same way they decide when to take a dependency upgrade, and until they do their gate keeps telling them the truth about the standard they are actually held to.

**Compared to the alternatives.** Puts the operator in charge of the timing without exempting anything permanently, and it makes adoption a visible decision with a visible cost rather than an ambush. It also allows a tree to sit on an old ruleset indefinitely, and it means the check's meaning now depends on a version — two vaults reporting clean are not necessarily held to the same standard.

**What would make this the wrong pick.** Versioned rules multiply. Every rule must keep working under every version anyone is still on, and the checking code accumulates conditionals for standards nobody has used in months — a maintenance cost paid forever for a disruption that happens occasionally.

## Definition of done

"Count how many existing rules would need a conditional to support two live versions"

```
npx vitest run test/knowledge/versioned-rule-cost.test.ts
```

Green means version awareness across the current rule set and its predecessor costs at most 5 conditionals, and the extrapolation to a year of tightenings stays under 20. Both are the node's own bars. It is red today because rules carry no version awareness at all, so there is nothing to count.

**This is a cost measurement, not a correctness one, and that is deliberate.** Nobody doubts versioned rules can be made to work. The question is whether the checking code accumulates conditionals for standards nobody has used in months — a permanent cost paid for an occasional disruption. A spec that only proved two versions could coexist would go green while saying nothing about the thing that would sink this.

**Read a green result pessimistically.** Two consecutive versions are the most similar pair available, so the count this produces is the optimistic end of the estimate by construction. The extrapolation clause exists precisely because the two-version number understates it; if the extrapolation is what fails, that is the honest signal and not a technicality.

**A precondition this row shares.** Nothing here can fire unless a build can tell which version wrote a given vault, which is "Check whether the writing version is recoverable from vault state at all" — red today for the same reason, and the cheaper of the two to answer first.

**What green does NOT settle.** Whether an operator whose tree is stranded out of compliance would rather be migrated than grandfathered. That is a preference about their own work and belongs to a person.

## History
- 2026-08-05 unlinked "Count how many existing rules would need a conditional to support two live versions" — moved under "Supporting two live ruleset versions costs few enough conditionals to stay maintainable" — the belief this test measures now has a node of its own
