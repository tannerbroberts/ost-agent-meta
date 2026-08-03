---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: At least 60% correct and at most 1 in 10 actively misleading.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that suggestions are more often right than misleading. A caller told "did you mean this other directory" will sometimes say yes when the real answer is that what they wanted does not exist and something is wrong upstream — and a helpful suggestion is how that goes unnoticed.

**Risk category: usability.**

**Design.** For every failed path lookup in the transcripts, generate the near-miss suggestion. A person who knows what the caller was actually after marks each as correct, unhelpful, or actively misleading. The misleading count is the one that decides this.

**Why it is small.** The failures exist and the intent is usually visible in the surrounding session. Generating suggestions is a few lines.

**What it will not cover.** Whether a caller would accept a wrong suggestion is a separate behavioural question this does not touch. The rate is a precondition, not the whole answer.

A human marks these and records the result.
