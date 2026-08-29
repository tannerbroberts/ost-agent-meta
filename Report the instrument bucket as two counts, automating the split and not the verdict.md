---
type: Solution
source: 'agent-run:unattended-sweep-2026-08-29'
created: '2026-08-29'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[The lane labels already stored are enough to split the bucket without inventing a judgement]]

**Variation dimension: automated-vs-manual. Position taken: automate the counting, leave the judgement manual on purpose.**

`ost_next_work` keeps every entry it holds today and stops reporting `solutionsMissingInstruments` as one number. It reports two: how many entries an unattended firing could actually act on, and how many are parked behind a verdict only a person can give. Nothing is hidden, nothing is written, and no verdict is inferred — the split is derived from the `lane` field already stored on each test, read through the `computeMayRun` predicate that `src/knowledge/lanes.ts` already exports and already fails closed on.

**What stays manual, and why that is the point rather than a shortfall.** Deciding that an entry is deliberate remains a human's `ost-agent lane --set`. This candidate makes no claim about any individual entry; it only refuses to add up two different kinds of thing. The parent node's complaint is that the operator "reads `65` as discovery debt and budgets compute against it" while the count of entries a firing can act on was, on that sample, zero. Two numbers fix the misreading without anyone adjudicating a single node.

**Contrast with the siblings.** The sibling granting the agent a humans-required verdict automates the judgement; the sibling adopting the disposition ledger automates the storage of a judgement a human makes at a CLI. This one automates neither — it is the only candidate that changes nothing about what is stored or who decides, and it is correspondingly the only one that cannot possibly file a wrong verdict.

**The honest cost of taking this position.** The queue does not shrink. An entry parked for seven passes is still listed on the eighth, just in the right column, so the re-derivation the parent calls a ratchet — a pass reading a node to work out that it is deliberate — is unchanged for anything whose lane was never set. This candidate improves the report and not the work.

**A second reason the split may be unavailable today.** It reads a lane label that most tests do not carry. The sweep already reports 473 tests in `needsHumans` against 0 `runnable`, which is `CAUTIOUS_LANE` doing its job on unlabelled tests rather than 473 considered verdicts — so the two columns would initially read "0 actionable, 65 parked" and overstate how much has been decided. Saying so on the report is part of this candidate, not an objection to it.

⚠️ Unvalidated, agent-ideated. No operator has said two counts would change how they budget.

## Definition of done

"The split reports defaulted-parked apart from labelled-parked, rather than folding both into one number"

```
npx vitest run test/mcp/instrument-bucket-split.test.ts
```

The spec does not exist yet, so this is `no-spec` today rather than assertion-red. The test node names the fixture: three solutions with prose-only tests — one lane `humans-required`, one lane `compute-only`, one with no lane — and asserts three figures come back, with the unlabelled solution landing in defaulted-parked rather than labelled-parked.

Note the title says *two counts* and the definition of done demands *three*. That is not a slip: the assumption beneath this solution is that the stored lane field distinguishes a considered verdict from `CAUTIOUS_LANE` defaulting, and this vault's own 473-needsHumans-against-0-runnable figure says it does not. A two-column build would go green on a two-column spec and reproduce the misreading this solution exists to prevent, so the third figure is the bar.
