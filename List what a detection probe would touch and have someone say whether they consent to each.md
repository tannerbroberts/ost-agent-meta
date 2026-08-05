---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  All 5 operators consent to every item, or a reduced list all 5 consent to
  still detects a credential.
instrument: npx vitest run test/security/auth-detection-report.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that probing for credentials is acceptable. A tool that enumerates the operator's secrets in order to be helpful has done something they may not have wanted, and a rejection reason reported back can leak more than the rejection.

**Risk category: usability, with an ethical dimension.**

**Design.** Write down exactly what the probe would read — which environment variables, which config paths, which CLI state — and what it would report about each. Show that list to five operators and ask, item by item, whether they consent. Record every refusal and what they objected to.

**Why it is small.** A list and five conversations, before anything reads anything.

**What it will not cover.** Consent given to a written list may differ from consent to the same probe running silently every startup. Asking specifically about that difference is worth adding.

A human runs this and records the result.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/security/auth-detection-report.test.ts — Asserts the report is emitted at startup before anything needs a credential, names which one will be used or why each found one was rejected, and never echoes a secret value — the node's own warning is that a rejection reason can leak more than the rejection. Red today because nothing probes for existing authentication or reports what it found.
