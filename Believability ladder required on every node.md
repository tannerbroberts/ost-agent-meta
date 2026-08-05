---
type: Solution
status: unvalidated
source: 'agent:P3_ideate'
created: '2026-07-24'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A visible evidence class changes how much a reader trusts the node carrying it]]

Make every node carry an explicit evidence class on a fixed ladder — money/retention > observed behavior > stated intent > expert opinion > founder or model assertion — and refuse to accept a node without one. The class is visible everywhere the node appears.

**How it differs from its siblings:** a per-node labelling discipline. Cheap and immediate, but purely local: it tells you what one node rests on, not what a conclusion drawn from many nodes rests on.

**Trade-off:** labels can be applied honestly and still mislead if nobody aggregates them; also adds friction to every write.

**Riskiest assumptions to test:** that a single ordering fits the evidence types this product actually sees (feasibility); that readers change their behavior when they see a low rung rather than ignoring the badge (desirability).

Status: agent-originated candidate. Unvalidated.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked "Labelled-vs-unlabelled branch comparison" — moved under "A visible evidence class changes how much a reader trusts the node carrying it" — the belief this test measures now has a node of its own

## Issues
- 2026-08-05 2026-08-05 Left un-instrumented because the mechanism already ships, and flagged instead for a status question. This node describes the ladder as a proposal — "refuse to accept a node without one", "the class is visible everywhere the node appears" — and both are live product behaviour. `ost_create_node` lists `evidence` among its required arguments and cannot be called without a rung; every node carries an `#evidence/<rung>` tag; `ost_set_evidence` caps the two measurement rungs by what the node points at and refuses above the ceiling; and the rollup aggregates to a weakest-rung-per-bucket, which answers the node's own stated weakness that "labels can be applied honestly and still mislead if nobody aggregates them". Any instrument I wrote for the described behaviour would pass on arrival, and the ruleset is explicit that a command which cannot fail measures nothing and hands a builder no definition of done. Same reasoning a prior pass applied to "A result must state what it did not cover" and to "Append-only tool surface with no delete or shell tool". What is left for a human is not a command but a bookkeeping question: this node is `status: unvalidated` while the thing it proposes is shipped and load-bearing across the whole tree, and its test — "Labelled-vs-unlabelled branch comparison" — asks whether readers change behaviour when they see a low rung, which is a desirability question about people and is untouched by the mechanism being live. Either the status should move to reflect what shipped, or the node's body should be rewritten to argue for the part that has not (the reader-behaviour claim), which is a product judgement rather than a sweep's call. Worth noting alongside it that the whole tree currently rests on `assertion` in every bucket, so the ladder is shipped, honest, and reporting a floor nobody has yet moved off.

## Definition of done

"Labelled-vs-unlabelled branch comparison"

```
npx vitest run test/ost/evidence-class-on-every-node.test.ts
```

Green means: "required on every node" is an invariant rather than a habit — `ost_check` fails a vault holding any unlabelled node, and the weakest-rung rollup is computed over every node, so an unlabelled one cannot silently flatter the floor. Green does **not** touch the test's threshold: 4 of 5 readers picking out the weakest-evidence node, and 3 changing their stated next action, needs five people.
