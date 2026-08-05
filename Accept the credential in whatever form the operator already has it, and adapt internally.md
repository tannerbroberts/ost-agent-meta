---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Count the distinct credential forms in play and how often each changed in a year]]

Widen what counts. Instead of demanding one credential type, accept every form the operator plausibly already holds — a session token, a CLI's stored auth, an OAuth grant, a personal access token, an environment variable set by something else — and translate internally to whatever the underlying call needs. The operator supplies what they have; the adaptation is the tool's problem.

**Compared to the alternatives.** The only option that actually unblocks the operator without depending on a host being present, so it works in cron, in a bare shell, and on a colleague's machine. It is also the most work by far and the most ongoing: every accepted form is a integration to maintain, and each one changes on someone else's schedule. Host delegation gets much of this for free where a host exists; detection merely explains the problem.

**What would make this the wrong pick.** Accepting many credential forms means handling many credential forms, and the safest thing a tool can do with a secret is not touch it. This route maximises exposure in exchange for convenience, which is precisely the trade a security-minded operator would refuse.

## Definition of done

[[Count the distinct credential forms in play and how often each changed in a year]]

`npx vitest run test/security/credential-forms.test.ts`

The spec asserts the adaptation this node makes the tool's problem: each form the operator plausibly already holds — session token, stored CLI auth, OAuth grant, personal access token, env var set by something else — resolves to the internal call shape, and none of them is echoed back to the caller. Red today because one credential type is demanded and no translation layer exists.

**What a green here does not settle.** The node's own objection, which is not about whether the code works: accepting many credential forms means *handling* many credential forms, and the safest thing a tool can do with a secret is not touch it. A passing spec proves the handling is correct and thereby proves the exposure is real — it is evidence for the objection as much as against it. Whether a security-minded operator accepts that trade is not a suite's question. Nor is the maintenance claim: every accepted form changes on someone else's schedule, and a green today says nothing about a year from now, which is precisely what the test's threshold was asking.
