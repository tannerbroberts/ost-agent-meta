---
type: Solution
source: 'CONVO:2026-08-11 operator session'
created: '2026-08-11'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Authors required to state a differentia produce discriminators, not boilerplate]]
[[A create-time guard can tell whether a differentia was supplied for each nearest sibling, without judging it]]

**Mechanism:** BFO's genus-differentia discipline moved to authoring time. Creating an Opportunity that would have siblings requires one extra argument: a sentence per nearest sibling naming a solution that would address the new node and not that sibling — Torres's interventional test, asked at the moment of writing instead of discovered by a later sweep. No differentia, no node.

**Contrast with the sibling "A decorrelation pass embedding screen, then evidence-extent verdict, then constant-comparative reframe":** that solution detects and repairs overlap after it accrues, paying adjudication cost every firing (its stage 2 flagged twelve pairs on its first day, and all twelve took judgement to clear). This one prevents the debt from accruing and costs nothing at sweep time. They compose rather than compete — but if prevention works, the repair pass's caseload should trend to zero, which is measurable.

**The honest risk:** required prose degrades into boilerplate. A differentia written to satisfy a gate ("this one is about X, that one is about Y") can restate the titles without discriminating anything, and a gate cannot tell. Whether authors under pressure produce real discriminators is the assumption beneath.

## Definition of done

"Create an opportunity beside an existing sibling with no differentia and require the refusal, then supply one per sibling and require the write"

```
npx vitest run test/ost/sibling-differentia-guard.test.ts
```

Green means the create path refuses an Opportunity that would gain siblings unless one differentia sentence per nearest sibling is supplied, refuses before anything is written, names the sibling left unaddressed, and writes the node with the sentences in its body when all are present — while still writing a first child with nothing extra. It is red today because the tool schema has no differentia argument and the hierarchy check never looks at the parent's other children; the spec does not exist yet either (no-spec red), so the builder's deliverable is the guard and the spec together.

It settles only that the gate can be built. Whether authors under it write discriminators rather than title-restating filler is "The operator grades the first ten differentia statements as discriminators or filler", which needs a person and stays humans-required.
