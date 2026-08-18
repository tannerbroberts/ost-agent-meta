---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  After redaction, 0 of the week's refusals reveal a node title, customer, or
  product decision.
instrument: npx vitest run test/security/refusal-redaction.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that the narrow slice is genuinely narrow. Refusal text can carry content — a refusal naming a node title leaks the node title — so making the boundary real is a redaction problem, and getting it wrong once destroys the trust the arrangement depends on.

**Risk category: feasibility.** Ethical exposure sits alongside it: this is about what leaves an operator's machine.

**Design.** Take every refusal this vault issued in one week, verbatim. Have a person read each as if they were an outsider and mark anything that reveals a node title, an opportunity, a customer, or a product decision. Then apply a candidate redaction rule and re-read to see what survives it.

**Why it is small.** The refusals are already recorded. Reading a week of them is an hour, and the result is a redaction rule or a demonstration that one is hard.

**What it will not cover.** One week of one vault, whose refusals are about this product. A vault about something commercially sensitive would have more to lose from the same text.

A human runs this and records the result.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/security/refusal-redaction.test.ts — The bar as written — "after redaction, 0 of the week's refusals reveal a node title, customer, or product decision" — is machine-checkable once a redactor exists: the spec runs every recorded refusal in the vault's trace through the redaction rule and asserts no surviving string matches any node title, vault path, or opportunity body in the tree. It fails today because no redactor exists, so every refusal quotes node titles verbatim.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/security/refusal-redaction.test.ts` — No test files found, exiting with code 1
- 2026-08-18 **green** (exit 0) `npx vitest run test/security/refusal-redaction.test.ts` — Duration  330ms (transform 23ms, setup 0ms, collect 24ms, tests 12ms, environment 0ms, prepare 39ms)
