---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  At least 3 of 5 name conditions they could actually satisfy, rather than
  declining outright.
instrument: npx vitest run test/security/credential-broker.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that operators will hand a long-lived secret to a local process that performs actions on their behalf. The whole design rests on that consent, and it is a bigger ask than any of the alternatives makes.

**Risk category: desirability.** Specifically willingness, not capability.

**Design.** Show five operators who run unattended agents the concrete arrangement — the broker, the scope language, the audit log — and ask what they would need to be true before they used it with a credential they actually hold. Ask about past behaviour: what have they already given an agent access to, and what have they refused. Do not ask whether they like the idea.

**Why it is small.** Five conversations, no build. The answer redirects the whole opportunity if it comes back negative, since the token and batching routes exist precisely for operators who will not do this.

**What it will not cover.** Stated willingness is not behaviour, and the ladder ranks it accordingly. Someone who says yes to a described broker may still decline the real one.

A human runs this and records the result.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/security/credential-broker.test.ts — Asserts the containment the node's whole argument rests on: the run receives the result of a scoped action and never the secret itself, and every request is logged with asker, target and outcome. Red today because no broker process, scope policy or request log exists.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/security/credential-broker.test.ts` — No test files found, exiting with code 1
- 2026-08-05 **green** (exit 0) `npx vitest run test/security/credential-broker.test.ts` — Duration  228ms (transform 30ms, setup 0ms, collect 33ms, tests 7ms, environment 0ms, prepare 27ms)
