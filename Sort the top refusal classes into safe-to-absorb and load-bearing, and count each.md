---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  At least 4 of the top 10 classes are judged safe to absorb, covering 30% or
  more of all refusals fired.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that a worthwhile share of recurring refusals exist for reasons that could be accommodated rather than enforced. Some refusals are load-bearing safety, and absorbing those is how a guardrail becomes decorative — so the question is how many are which.

**Risk category: feasibility.**

**Design.** Take the ten most frequent refusal classes from the harvested record. For each, a person decides: is this refusal protecting against something real, or is it enforcing a convention the tool could simply have honoured? Record the reason for each verdict alongside the frequency, so the count is weighted by how often the class actually fires.

**Why it is small.** Ten judgements against a frequency table that already exists.

**What it will not cover.** The judgements are made by the person who wrote most of these refusals, which biases toward believing each was necessary. It also cannot tell whether absorbing a class is technically feasible — only whether it would be safe.

A human runs this and records the result.
