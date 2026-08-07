---
type: Solution
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Every short category has a leaf beneath it that is genuinely under-served]]

**The idea.** When the sweep finds a category short of solutions, it does not report the category. It walks down to the leaf opportunities beneath it and reports whichever of those are actually under-served. If none are, it reports nothing for that branch.

**Why this shape.** The queue's job is to name the next thing to do, and a category is never the next thing to do — a solution cannot legitimately hang there. Both siblings fix the miscount; only this one guarantees that every entry in `underservedOpportunities` is a node where the instruction "ideate three solutions" is a valid instruction. That is a stronger property than being numerically correct, and it is the property the observed failure actually needed: the pass on 2026-08-07 was not confused about the numbers, it was handed 24 headings and had to work out by hand which were real.

**How it compares to its siblings.**
- Rollup makes the number right; this makes the *entry* right. Rollup would still list a genuinely thin category and leave the pass to find the leaf itself.
- Exemption makes categories silent; this makes them transparent — the branch still produces work when there is work, which is the false-negative that exemption cannot avoid.

**Where it fails, stated so it can be judged.** It is the most code this branch could take. Descending requires a traversal per short category and a rule for what to do when a leaf is under-served in several branches at once, and a badly-shaped tree — a category whose leaves are all served but whose own need is not covered by any of them — produces silence with no explanation, which is the same failure as exemption arriving by a longer road.

**Cost.** Highest of the three. A traversal, an ordering rule, and fixtures for the empty-descent case.

⚠️ Unvalidated. Agent-ideated.

## Definition of done

"Descending to leaves never returns silence without a reason"

```
npx vitest run test/ost/next-work-leaf-redirect.test.ts
```

Written without repo sight, so its first red is an absent file. The bar is the diagnostic on an empty descent, not the count.
