---
type: Solution
source: 'TRANSCRIPT:9c00df65-1c8d-4171-a870-22efc103d834'
created: '2026-09-03'
evidence: assertion
killIf: >-
  A caller's first three real searches cannot be expressed in the structured
  form without an escape hatch to a raw pattern.
killBy: '2026-12-01'
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[The searches callers actually run can be expressed as declared intent without dropping to a raw pattern]]

**Variation dimension: who-does-the-work. Position: nobody — the step is removed.** The other two candidates keep the caller composing a pattern and differ on who explains the boundary; this one deletes the composing step, so no party has to learn or publish a dialect at all.

The caller says what it is looking for in structured terms — a literal string, a whole word, a line containing A and not B, a value in a named field — and the surface compiles that into whatever the underlying engine actually supports. Look-around never has to be written because the intent "A not followed by B" is expressed as a field, and the compiler decides whether that becomes a negative look-ahead, a two-pass filter, or a post-filter in the caller's own process.

**What it buys.** The failure recorded in the evidence cannot occur: there is no construct to reach for that the engine might not have, because the caller never names constructs. The boundary of the engine stops being something a caller discovers and becomes something the compiler absorbs.

**What it deliberately gives up, stated plainly.** Expressive reach. Every pattern a structured surface cannot express is a search that used to be possible and now is not, and the caller's escape hatch — dropping to a raw pattern — reintroduces the whole problem for exactly the cases that most needed it. That is the trade this candidate takes and the sibling candidates refuse.

**Where this would live in the product.** Nothing in this repo currently accepts a regex from a caller, so this candidate is about the shape of a surface this product does not yet have rather than a change to one it does. It is written because the same shape already recurs here in a non-regex form: `instrument` refuses shell punctuation, `threshold` demands a comparator, and each is discovered one refusal at a time.

## Provenance

Ideated by an unattended sweep on 2026-09-03 against the assigned variation dimension `who-does-the-work`. Rests on the parent opportunity's evidence and on nothing else; no customer has asked for this shape.
