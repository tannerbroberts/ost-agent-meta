---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  0 nodes have their meaning changed, and every touched node is listed in the
  migration's own report.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that mechanical migration is safe. It is a bulk rewrite of a record that is supposed to be append-only, and even done carefully it changes what nodes say without a human reading them — which for a vault whose whole claim is a trustworthy history may be too much to hand to a script.

**Risk category: feasibility, with a real ethical dimension** given what append-only is for.

**Design.** Pick one past tightening and write the migration it should have shipped with. Run it on a copy. Have a person read every node it touched, before and after, and mark any where the meaning changed rather than the form. Count.

**Why it is small.** One rule, one copy of the vault, a bounded set of touched nodes.

**What it will not cover.** An easy tightening will migrate cleanly and say little about a hard one. Choosing the most awkward past tightening rather than the most convenient is what makes this worth running.

A human reads the diff and records the result.
