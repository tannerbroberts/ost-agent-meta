---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Compute the unblocking order and compare it against what the builder actually picked up]]

The tree computes, for every actionable item, how much else is waiting behind it, and presents the frontier in that order. The top of the list is whatever the most work is currently blocked on — not the cheapest thing, not the highest-scoring thing, but the one whose absence is costing the most elsewhere.

Efficiency in a dependency graph is not a property of individual steps. A cheap step that unblocks nothing is worse than an expensive one that unblocks nine, and any ordering that reads items one at a time cannot see the difference.

**Compared to the alternatives.** This asks nothing of the operator and nothing of a model — it is a computation over edges the tree already has, which makes it the cheapest route to a defensible order. What it cannot do is weigh how much any of it matters: it will happily put a heavily-depended-upon branch at the top of the list when the whole branch is aimed at something nobody wants. Sizing and importance are genuinely human inputs, and this deliberately does not ask for them.

**What would make this the wrong pick.** It rewards whatever the tree has recorded most densely. A branch that is well-mapped because it was easy to map will outrank a sparse branch that matters more, and the ordering will look rigorous while doing it.

## Definition of done

[[Compute the unblocking order and compare it against what the builder actually picked up]]

```
npx vitest run test/ost/frontier-unblocking-order.test.ts
```

Green means: the order exists and is the one this solution names — each item reports how many others its completion unblocks, sorting is by that count rather than title or cost, and an item that unblocks nothing sorts last however cheap it is. Today the frontier is alphabetical and capped at 25, which is neither. Green does **not** perform the comparison; what a builder actually picked up is a record of human behaviour and reading it against the computed order is a person's job.
