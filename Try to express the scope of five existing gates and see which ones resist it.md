---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  At least 3 of 5 scopes are expressible without a clause that could be
  satisfied vacuously.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that a gate's intended coverage can be written down up front. That is easy for files and hard for behaviours, and a scope that cannot be expressed cannot be enforced.

**Risk category: feasibility.**

**Design.** Take five gates this project already has. For each, attempt to write its intended coverage in a form a program could check — which files, which cases, which behaviours must be exercised. Record which succeed cleanly, which need a vague clause, and which cannot be written at all. Note whether the vague ones could be satisfied by keeping the scope and hollowing out what happens inside it.

**Why it is small.** Five gates already exist. The exercise is writing, and failing to write is the result.

**What it will not cover.** Whether an author would keep the scope current as the gate's purpose evolves — which is where a written scope most plausibly rots.
