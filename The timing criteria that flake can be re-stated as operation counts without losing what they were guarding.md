---
type: Assumption
created: '2026-08-07'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

The solution rests on a translation being available. Every timing gate that currently flakes has to have an operation-count form that guards the same thing the wall-clock form guarded.

This could be false in either direction. It fails if the flaky criteria turn out to be predominantly about human-perceived latency — "the status view returns before the operator gives up" — because no count of reads is a substitute for that, and re-stating it as one would replace a guard that meant something with a guard that passes while the product feels slow. It also fails if the dominant cost is not countable at the seam available: time spent inside a single subprocess call is one operation and any duration at all, so a gate over a shelling-out step would count 1 and guard nothing.

A feasibility assumption, and one the repository can answer: which criteria exist, what each asserts, and whether its cost is concentrated in countable operations or inside opaque calls are all facts on disk. It does not need anyone's afternoon.

## What a passing test here would NOT settle

That the counted form is cheap to maintain, that operators trust a gate expressed in reads as readily as one expressed in milliseconds, or that the instrumented counting seam is itself correct. Feasibility answered mechanically leaves desirability, viability and usability exactly where they were.
