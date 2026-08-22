---
type: Solution
source: 'CONVO:2026-08-11 operator session'
created: '2026-08-11'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The operator reads sweep-chosen work order as ordering, not as target selection]]
[[Grouping ost_next_work's buckets by branch withholds no item the flat listing would have shown]]

**Mechanism:** `ost_next_work` emits every bucket grouped by branch instead of tree-walk (effectively alphabetical) order — all of one region's outstanding items surface together, and the next region is not sampled until the first reports clean. The observed failure this answers is the display-capped alphabetical slice: fourteen consecutive passes re-deriving the same global queue and finishing no region of it.

**Contrast with the sibling "A discovery firing scoped to one human-chosen target branch, worked to done before the sweep widens":** that solution produces dwell only after a human writes `discovery.target`; this one produces dwell with no human act, on the unscoped sweep that actually runs when no target is set — which, as of the firing that ideated this, is every firing, because the shipped target mechanism is still unset.

**The viability risk is the ruleset itself, named rather than papered over:** `ruleset.ts` MUST NOT auto-select a target opportunity. Ordering all work is not declaring a target — every bucket item is still emitted and nothing is withheld — but the region worked *first* becomes an agent choice, and whether the operator reads that as ordering or as selection is exactly the question the assumption beneath this must settle before anyone builds it.

## Definition of done

"The branch-grouped sweep emits the same item set as the flat sweep, only reordered"

```
npx vitest run test/mcp/branch-grouped-buckets.test.ts
```

Red today because the spec is not written and `ost_next_work` has no branch-grouped mode to write it against; green when grouping exists and withholds nothing. Written blind of an existing spec file, so its first observation will file as `no-spec` — the bar above is what carries a builder, per this repo's own `confirmPermit` rule.

**This command settles feasibility only.** The viability question this candidate actually turns on — whether the operator reads a sweep-chosen order as target selection, forbidden by the ruleset's auto-select rule — is "Ask the operator, ruleset line in hand, whether sweep-chosen order violates their auto-select rule", and no exit code answers it. A green here must not be read as clearance to build.
