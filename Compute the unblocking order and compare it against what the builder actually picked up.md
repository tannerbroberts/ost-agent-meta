---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  The computed order diverges on at least 2 of 5, and the builder prefers the
  computed choice in at least 1.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that dependency-weighted order is useful advice — that it differs from what the builder would have chosen unaided, and that where it differs it is better. An ordering that merely agrees with existing instinct is free confirmation and no help.

**Risk category: usability.**

**Design.** Compute the ordering over the current tree but do not show it. Ask the builder to name the five things they would pick up next, in order, and write those down. Then reveal the computed order and compare. For each divergence, the builder says which they now think is right and why.

**Why it is small.** The computation is a graph walk over edges the tree already has, and the comparison is one conversation.

**What it will not cover.** A builder shown a computed order will tend to find reasons it is right. Collecting their five first, in writing, is what makes this worth anything, and even so it is one builder on one tree.

A human runs this and records the result.
