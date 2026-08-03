---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  At least 3 of 5 name conditions they could actually satisfy, rather than
  declining outright.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that operators will hand a long-lived secret to a local process that performs actions on their behalf. The whole design rests on that consent, and it is a bigger ask than any of the alternatives makes.

**Risk category: desirability.** Specifically willingness, not capability.

**Design.** Show five operators who run unattended agents the concrete arrangement — the broker, the scope language, the audit log — and ask what they would need to be true before they used it with a credential they actually hold. Ask about past behaviour: what have they already given an agent access to, and what have they refused. Do not ask whether they like the idea.

**Why it is small.** Five conversations, no build. The answer redirects the whole opportunity if it comes back negative, since the token and batching routes exist precisely for operators who will not do this.

**What it will not cover.** Stated willingness is not behaviour, and the ladder ranks it accordingly. Someone who says yes to a described broker may still decline the real one.

A human runs this and records the result.
