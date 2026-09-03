---
type: AssumptionTest
source: 'TRANSCRIPT:9c00df65-1c8d-4171-a870-22efc103d834'
created: '2026-09-03'
evidence: assertion
threshold: >-
  all 3 unsupported constructs named in one refusal, and 0 false flags across at
  least 12 supported patterns
instrument: npx vitest run test/guards/pattern-dialect-preflight.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

Submit a pattern containing a look-ahead, a backreference and a possessive quantifier to the pre-flight validator and assert the single refusal names all three, each with its offset. Then submit a battery of patterns that use only supported constructs — character classes, non-capturing groups, alternation, anchors, lazy quantifiers, unicode classes — and assert none of them is flagged.

The second half is the half that matters and the half a validator author is most likely to skip: a parser that refuses everything it does not recognise passes the first assertion and is useless.

**Lane: compute-only.**

**What this does NOT settle.** Only that the constructs can be located. It says nothing about whether the one-refusal form actually saves a caller calls in practice, nothing about whether callers prefer it to a structured surface, and nothing about the parser staying correct when the underlying engine changes version — that last is a separate assumption nobody has written yet.
