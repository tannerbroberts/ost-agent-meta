---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Try to derive the seven questions from the premise alone, before reading the session]]

Before starting, work out what the stated premise implies and present the whole set together: here are the seven decisions that follow from this, here is what each depends on, here is the default proposed for each. The operator answers once, in one sitting, seeing the shape of the whole thing. The run then proceeds without stopping again unless it meets something genuinely outside what was covered.

Answering seven questions at once is a different act from answering seven questions in sequence. Together they can be made consistent, and the operator can see that question four is why questions five through seven exist.

**Compared to the alternatives.** Removes the interruptions rather than deferring them, and it front-loads the operator's attention when they are already thinking about the change. It requires deriving consequences correctly in advance, which is exactly what the session failed to do — and a derivation that misses three of the seven leaves the run stopping anyway, having also spent the operator's time on a batch.

**What would make this the wrong pick.** Some of those seven only became visible after work was done — the duplicated refusal template, the severed ingestion — and no amount of up-front thinking would have surfaced them. Against genuinely emergent questions this offers nothing.

## Definition of done

[[Try to derive the seven questions from the premise alone, before reading the session]]

`npx vitest run test/loop/premise-consequence-set.test.ts`

The spec asserts the shape: the consequence set is derived from the stated premise **before** the run begins, presented as one batch with each item's dependency and its proposed default, and the run then proceeds without stopping again unless it meets something outside the covered set. The dependency links are load-bearing — the node's argument is that answering seven at once differs from seven in sequence precisely because the operator can see that question four is why five through seven exist. Red today because nothing derives consequences up front.

**What a green here does not settle, and it is what decides the node.** Whether the derivation is *complete*. The test asks someone to derive the seven questions from the premise alone and compare against what the session actually hit — and the node already concedes that some of them only became visible after work was done, the duplicated refusal template and the severed ingestion among them. A derivation that misses three of seven leaves the run stopping anyway, having also spent the operator's attention on a batch. A spec can prove the batch was presented; only the blind derivation shows what it left out.
