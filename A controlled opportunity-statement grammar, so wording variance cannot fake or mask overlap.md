---
type: Solution
source: 'CONVO:2026-08-11 operator session'
created: '2026-08-11'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A reader still recognizes their own need after normalization]]
[[Normalization raises the similarity score of two statements of one need above the bar their raw wording fails]]

**Mechanism:** an Ulwick-style controlled grammar for opportunity statements — situation, struggle, desired progress, in the customer's voice — applied as a normalization step before any comparison runs. Two statements of one need converge toward one wording; two needs stop being mistaken for one because they happened to share vocabulary. This attacks the exact blind spot the parent records: title-token Jaccard scored two names for the identical work item at 0.29, and no extent arithmetic can see overlap between nodes whose citations are disjoint.

**Contrast with its siblings:** the decorrelation pass compares citations (extent), which is blind to wording; the differentia gate disciplines new siblings, which does nothing for the hundred-plus statements already written. Normalized wording is the only one of the three that makes *lexical* comparison trustworthy, and it is upstream of both — a screen over normalized statements nominates better pairs, and a differentia is easier to state against a normalized sibling.

**The honest risk is Torres's own requirement:** opportunity statements carry the customer's voice, and normalization is a rewriting. A grammar that makes statements comparable by making them all sound like the grammar has traded the method's raw material for tidiness. Whether a reader still recognizes their own need in the normalized form is the assumption beneath.

## Definition of done

"Normalized duplicate pairs clear the dedupe bar that their raw titles fail, and distinct siblings stay below it"

```
npx vitest run test/ost/statement-grammar.test.ts
```

Two-sided over at least 8 human-judged pairs: confirmed duplicates cross 0.50 only after normalization (the parent's motivating case scored 0.29 raw), and no confirmed-distinct sibling crosses it at all. The second half is what stops a normalizer that flattens everything into the grammar's vocabulary from passing — that version lifts every score and makes the dedupe screen useless.

Named in plain quoted text rather than as a wikilink: the test is linked exactly once, by the Assumption above it.

**This covers the feasibility half only.** The desirability risk this node names as the honest one — whether a reader still recognizes their own need after the rewriting — is the other assumption beneath this solution, needs actual readers, and is untouched by any green here.

_Added 2026-08-21: this solution carried only its desirability assumption, so the whole node read as human-only work when half of it is settled by code and fixtures._
