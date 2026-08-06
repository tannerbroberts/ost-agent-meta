---
type: Solution
source: 'agent-ideation:2026-08-06-unattended-sweep'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A provenance census would not have flagged the three guards that motivated it]]

**The idea.** Do not fix anything yet. Walk every assertion in the suite and trace where each side came from. Report the ones where the expected value and the actual value trace back to the same module, constant, or generator — the shape that cannot disagree. The output is a list with a number on it, not a repair.

**Why this shape.** The parent opportunity's most honest sentence is its last: *"Nobody has counted how many of this repo's checks have that shape — the honest answer today is that one of them was found by accident, while chasing something else."* Every other response to this opportunity presumes an answer to a question nobody has asked. If the population is three, a policy is overkill and a mutation harness is absurd. If it is ninety, the tree's believability argument — which rests entirely on gates trusted because they are mechanical — is resting on something nobody has inspected, and that is a different and much larger finding than the bug that started it.

**How it differs from its siblings.** It is the only one that is read-only, the only one that produces a number rather than a mechanism, and the only one whose value does not depend on being right about the fix. Its siblings are both *responses*; this is the measurement that says which response is proportionate. It is also the cheapest by a wide margin, which matters for an opportunity discovered by accident and not yet sized.

**Where it fails, stated so it can be judged.** Provenance tracing through TypeScript is approximate — a value passed through two helpers and a destructure is hard to attribute, and the analysis will produce both false positives (an expectation that legitimately shares a constant with the subject because the constant *is* the contract) and false negatives (shared assumptions that never appear as a shared symbol, which is arguably the more dangerous half). It also finds only the syntactic form of the disease. Two guards written independently from the same wrong belief in someone's head share no symbol at all and are exactly what happened here — three files derived the prefix *independently*, which this census might well score as three unrelated checks.

That last caveat is severe enough to state as a limit rather than a footnote: this census would probably not have found the bug that motivated it. It would find a related population, and knowing that population's size is still worth more than the guesswork currently standing in for it.

**Cost.** A one-off analysis script and a reading. No product change, no CI time, nothing to maintain if the answer is small.

⚠️ Unvalidated. Agent-ideated, from the agent's own repository.

## Definition of done

"Score the provenance census against the three guards it was invented to catch"

```
npx vitest run test/guards/provenance-census-scores-against-known-defects.test.ts
```

Green means the census flags all three known-defective prefix guards. This node's own body predicts it will not — the three derived the prefix independently and share no symbol — and the test exists to settle that prediction rather than leave it as a caveat. A red is the expected and informative outcome: the census may still be worth building to size the syntactically self-derived population, but it would have to be re-described as measuring a related population rather than as an answer to this opportunity.

Named in plain text rather than linked: the test's one wikilink is held by its parent assumption, "A provenance census would not have flagged the three guards that motivated it".
