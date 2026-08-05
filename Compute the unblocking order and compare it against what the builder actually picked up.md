---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  The computed order diverges on at least 2 of 5, and the builder prefers the
  computed choice in at least 1.
instrument: npx vitest run test/ost/frontier-unblocking-order.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that dependency-weighted order is useful advice — that it differs from what the builder would have chosen unaided, and that where it differs it is better. An ordering that merely agrees with existing instinct is free confirmation and no help.

**Risk category: usability.**

**Design.** Compute the ordering over the current tree but do not show it. Ask the builder to name the five things they would pick up next, in order, and write those down. Then reveal the computed order and compare. For each divergence, the builder says which they now think is right and why.

**Why it is small.** The computation is a graph walk over edges the tree already has, and the comparison is one conversation.

**What it will not cover.** A builder shown a computed order will tend to find reasons it is right. Collecting their five first, in writing, is what makes this worth anything, and even so it is one builder on one tree.

A human runs this and records the result.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/ost/frontier-unblocking-order.test.ts — The comparison needs a computed order to compare against, and the tree produces none — the frontier comes back as an alphabetical list capped at 25, which is neither an ordering nor a ranking. This asserts the computation: each frontier item reports how many other items its completion would unblock, the order is by that count rather than by title or cost, and an item that unblocks nothing sorts last no matter how cheap it is. Missing-spec red, not assertion red: the pass holds no repo-read grant, so the file is absent; a builder should write it against the real frontier query so it goes red on the alphabetical ordering that ships today. It does not settle the comparison itself — what a builder actually picked up is a record of human behaviour, and reading it against the computed order is a person's job.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/ost/frontier-unblocking-order.test.ts` — No test files found, exiting with code 1
