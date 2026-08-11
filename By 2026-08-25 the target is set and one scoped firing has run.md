---
type: AssumptionTest
source: 'observation:2026-08-11 ost_next_work returned no scope field'
created: '2026-08-11'
evidence: assertion
lane: humans-required
threshold: >-
  By 2026-08-25 (two weeks after PR #100 shipped), discovery.target names a real
  Opportunity and at least one firing has returned a scope field — otherwise the
  assumption fails.
---
#AssumptionTest #unvalidated #evidence/assertion

**Small, fast, and already running:** the mechanism shipped 2026-08-11 with the operator's stated demand behind it, so the test is simply whether the enabling act happens within two weeks. Any firing can read the verdict from its own `ost_next_work` response: a `scope` field present means set, absent past 2026-08-25 means the assumption failed.

**What a failure would mean:** not that the operator lied — that a mechanism whose first act is spending an operator-hour is mis-designed for an operator with none, and the sibling candidates that need no human act (bucket ordering, a deep-dive firing type) deserve the next build instead.

**What this does not settle:** whether scoped firings actually produce better discovery — only whether the switch gets flipped. Effectiveness is a separate assumption for after the first scoped passes exist.

A person outside the building is the measurement here: Only the operator can set discovery.target — no tool can write it, by design — so the measurement is irreducibly whether they perform the act.
