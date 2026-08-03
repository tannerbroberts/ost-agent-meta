---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  0 of 10 starts silently select the wrong vault; ambiguous cases return nothing
  rather than guessing.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that upward search is unambiguous. It silently binds a project to whatever vault happens to sit above it, and on a machine with several vaults that produces no error at all — only the wrong tree.

**Risk category: feasibility.**

**Design.** This machine already has more than one vault. Construct the realistic layouts — a project nested under one vault while another sits at the home directory, two vaults as siblings, a project outside any vault — and run the upward search from ten starting directories. Record how often it finds the intended vault, the wrong one, or nothing.

**Why it is small.** The search is a few lines and the layouts already partly exist. Ten runs.

**What it will not cover.** The intended vault is decided by the person constructing the test, and in ambiguous layouts there may be no objectively correct answer — which is itself worth recording as a finding rather than resolved by fiat.
