---
type: AssumptionTest
created: '2026-08-22'
evidence: assertion
threshold: >-
  zero records unlabelled, offered equals read, and the fired count is
  monotonically non-increasing across bars 1 to 10
instrument: npx vitest run test/friction/threshold-sweep.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** This measures whether a count survives as data, which is a fact about the records and the reader, not about anyone's preference.

**Design.** Over a fixture set of stored friction records, sweep candidate bars N = 1..10 and label every record fired / not-fired at each. Assert the sweep reports a denominator alongside its counts — how many records it was offered and how many it could read — so a reader that silently skipped the records it could not parse comes out as blind rather than as clean. This repo already draws exactly that distinction in `src/ost/sweep.ts`; the point here is that this reader is held to it too.

**Pre-committed threshold:** zero records come back unlabelled, the offered and read counts are equal, and the fired count is monotonically non-increasing as N rises.

**Why the monotonicity clause is in the bar.** It is the cheapest check that the labelling means what it says: a reader that mis-parses counts can still label everything, and a fired count that goes up as the bar rises is the signature of that failure. A label per record is not evidence the labels are right.

**What this does not settle.** Nothing about whether the bar is a good one. Whether an operator agrees with the verdicts is the sibling assumption's study — "Show the operator a handful of recorded sessions and the threshold's would-have-fired verdict, and ask which they'd have wanted alerted" — which this exists to make assemblable, not to replace.
