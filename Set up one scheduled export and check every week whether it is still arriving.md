---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: '8 of 8 weekly checks find a current file, with no silent gap.'
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that a scheduled export, once configured, keeps arriving. The failure this solution's own reasoning fears is a silent stop — an expired link, a renamed sheet — which looks identical to an experiment that produced nothing. If that happens quickly, the route replaces a human who forgets with a mechanism that fails invisibly.

**Risk category: feasibility.**

**Design.** Configure one export from a real source into the watched folder. Each week for eight weeks, check whether the expected file arrived and whether its contents are current. Record every gap and its cause.

**Why it is small.** Configuration only, no code, and the checking is a minute a week.

**What it will not cover.** Eight weeks will not catch annual credential expiry, which is a likely cause of exactly this failure. It also tests one source configured carefully by someone who knows it matters.
