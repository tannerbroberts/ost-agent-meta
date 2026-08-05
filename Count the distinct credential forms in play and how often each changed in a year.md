---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  At most 6 forms, with fewer than 4 breaking changes across all of them in the
  last year.
instrument: npx vitest run test/security/credential-forms.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that the set of credential forms is small and stable enough to maintain. Every accepted form is an integration, and each one changes on someone else's schedule — so the ongoing cost is the question, not the initial build.

**Risk category: feasibility.**

**Design.** Enumerate the credential forms this tool would need to accept for the services it actually touches. For each, look back a year through changelogs and deprecation notices and count breaking changes. Total the annual maintenance events.

**Why it is small.** Reading public changelogs for a handful of services, an afternoon.

**What it will not cover.** Past change rate predicts future change rate poorly for services that are themselves young. It also says nothing about the security exposure of handling many forms, which is the other half of the objection and needs a different test.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/security/credential-forms.test.ts — Asserts the adaptation this node makes the tool's problem: each form the operator plausibly already holds — session token, stored CLI auth, OAuth grant, personal access token, env var set by something else — resolves to the internal call shape, and none is echoed back to the caller. Red today because a single credential type is demanded and no translation layer exists.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/security/credential-forms.test.ts` — No test files found, exiting with code 1
