---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

Make the expectation explicit in the ruleset the pass follows: read the sweep once at the start, work from it, and re-read only at the end to confirm. A pass that wants an extra read states what it did that could have changed the answer. The discipline is written down rather than left to judgement, and departures from it become visible in the record.

This is the cheapest possible intervention, because nothing is built. The ruleset already shapes how a pass behaves in a dozen other ways, and this is one more line in it.

**Compared to the alternatives.** Free, immediate, and it works on the current tool surface with no change to anything. It is also the weakest by a distance: it is a rule addressed to a caller, and the whole reason this opportunity exists is that a caller with a rule available did the thing anyway. Caching and returned deltas both make the right behaviour cheap; this only asks for it.

**What would make this the wrong pick.** Rules that constrain reads make a pass less careful, and a pass that is uncertain whether its picture is current will either act on stale information or spend the call and feel bad about it. Trading correctness for a cheaper trace is the wrong direction if the re-reads were doing real work — and nothing here establishes that they were not.
