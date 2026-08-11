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

## What a green run does not settle

Byte-identical prose plus a red-to-green `check` is a strong mechanical stand-in for "changed nothing's meaning", and it is not the same claim. It proves the migration touched structure and frontmatter only. A migration can leave every word intact and still change what a node *means* by re-parenting it under a different opportunity — the prose is untouched, the claim it makes in context is not.

So the reader in this test's title has not been made redundant, only made cheaper: they no longer have to diff the wording, and can spend their attention on the handful of nodes whose position moved. If that set is large, this instrument passing should not be read as the test passing.

It also covers exactly one past tightening. Generalising from that to "migrations ship with tightenings and it works" is the inference this evidence cannot support.

## Instrument Log
- 2026-08-07 **red** (exit 1) `npx vitest run test/ost/tightening-migration-meaning.test.ts` — No test files found, exiting with code 1
- 2026-08-11 **green** (exit 0) `npx vitest run test/ost/tightening-migration-meaning.test.ts` — Duration  346ms (transform 90ms, setup 0ms, collect 134ms, tests 17ms, environment 0ms, prepare 26ms)
