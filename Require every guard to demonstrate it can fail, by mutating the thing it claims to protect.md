---
type: Solution
source: 'agent-ideation:2026-08-06-unattended-sweep'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The three guards that agreed with the bug would stay green under a mutation of the thing they check]]

**The idea.** For each guard, break the property it claims to protect and require the guard to go red. A guard that stays green while its subject is deliberately wrong is not a guard, and the suite says so by name rather than by counting coverage.

**Why this shape.** The parent opportunity states the disease precisely — *"a check that computes the thing it is checking cannot fail when the computation is wrong; it can only fail when the two sides disagree, and they never disagree if they share an assumption."* That is a statement about a guard's **reachable failure set**, and mutation is the only technique here that interrogates it directly. The three prefix guards would have been caught on day one: mutate the manifest's server name, and a guard that derives its expectation from that same manifest follows the mutation and stays green. No reading of the code is required to notice; the green is the evidence.

**How it differs from its siblings.** Its siblings look at how a guard is *written* — one constrains the expectation's source, the other counts guards with a suspicious shape. Both can be satisfied by a guard that is still, in fact, unable to fail. This one ignores how the guard is written and measures the only property that matters. It is also the only one of the three that produces a per-guard verdict rather than a policy or a list.

**Where it fails, stated so it can be judged.** Mutation is expensive and this is its expensive form — one suite run per mutant, against a suite already at 480+ tests. Choosing the mutations is a judgement, and a mutation set authored by the same party that authored the guards will share blind spots with them, which is this opportunity's own disease reappearing one level up. It says nothing about guards that are missing entirely: you cannot mutate your way to a property nobody thought to protect.

**Cost.** Substantially the largest of the three. A mutation harness, a curated mutant set per guard, and CI time — against a repository whose perf gates are already noted as fragile under load.

⚠️ Unvalidated. Agent-ideated. No operator has asked for this, and its cost is real enough that a census should probably run first to size the population it would be applied to.

## Definition of done

"Mutate the manifest server name and require the three prefix guards to go red"

```
npx vitest run test/guards/mutation-detects-self-derivation.test.ts
```

Green means all three known-defective prefix guards go red under a mutation of the manifest field they derive from — the technique catching the case that motivated it, scored against ground truth. Three of three, not a majority: a technique that misses one of the three known cases has no claim on the unknown ones. Run "Census every check whose expected and actual sides are drawn from the same source" first if cost is a concern; this is the most expensive of the three siblings and the census sizes the population it would be applied to.

Named in plain text rather than linked: the test's one wikilink is held by its parent assumption, "The three guards that agreed with the bug would stay green under a mutation of the thing they check".
