---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  0 nodes have their meaning changed, and every touched node is listed in the
  migration's own report.
instrument: npx vitest run test/ost/tightening-migration-meaning.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that mechanical migration is safe. It is a bulk rewrite of a record that is supposed to be append-only, and even done carefully it changes what nodes say without a human reading them — which for a vault whose whole claim is a trustworthy history may be too much to hand to a script.

**Risk category: feasibility, with a real ethical dimension** given what append-only is for.

**Design.** Pick one past tightening and write the migration it should have shipped with. Run it on a copy. Have a person read every node it touched, before and after, and mark any where the meaning changed rather than the form. Count.

**Why it is small.** One rule, one copy of the vault, a bounded set of touched nodes.

**What it will not cover.** An easy tightening will migrate cleanly and say little about a hard one. Choosing the most awkward past tightening rather than the most convenient is what makes this worth running.

A human reads the diff and records the result.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/ost/tightening-migration-meaning.test.ts — Meaning-preservation has a mechanical form for this vault — run the migration over a tree fixture captured before a past tightening and assert every node's prose is byte-identical afterwards while `check` goes from red to green, so the migration is proven to have moved structure and not wording; it fails today because no migration and no before-tightening fixture exist.
