---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Operators consent to a probe that looks in the places their credentials live]]

At startup, look for the credentials the operator already has — the CLI that is logged in, the environment variable that is set, the config file that exists — and report what was found and which one will be used, before anything needs it. If none will serve, say so then, naming the ones that were found and why each was rejected.

The frustration this addresses is largely informational. Being asked for a credential is bearable; being asked while already authenticated, with no explanation of why the existing one will not do, is what makes it feel absurd.

**Compared to the alternatives.** Cheap, works everywhere, and needs no cooperation from any host. It does not actually let the existing credential be used — it only explains, and an operator who wanted to be unblocked has been given a clear account of why they are not. Borrowing the host's authority solves the problem; this makes the problem legible.

**What would make this the wrong pick.** Probing for credentials means touching places credentials live, and a tool that enumerates the operator's secrets to be helpful has done something they may not have wanted. What it looks at and what it reports both need care, and reporting a rejection reason can leak more than the rejection.

## Definition of done

[[List what a detection probe would touch and have someone say whether they consent to each]]

`npx vitest run test/security/auth-detection-report.test.ts`

The spec asserts the report is emitted at startup, *before* anything needs a credential — which is the whole point, since being asked while already authenticated is what the node identifies as the actual frustration — and that it names which credential will be used, or which were found and why each was rejected. It also asserts no secret value is ever echoed, because the node's own warning is that a rejection reason can leak more than the rejection. Red today because nothing probes or reports.

**What a green here does not settle.** Consent. Probing for credentials means touching the places credentials live, and a tool that enumerates the operator's secrets to be helpful has done something they may not have wanted — a spec can verify the probe touches only a declared list, and cannot ask anyone whether they agree to that list. That is exactly what the test's title asks a person to do. Note too that this candidate never unblocks anyone: it makes the problem legible, and an operator who wanted to proceed has been handed a clear account of why they cannot.

## History
- 2026-08-05 unlinked [[List what a detection probe would touch and have someone say whether they consent to each]] — moved under [[Operators consent to a probe that looks in the places their credentials live]] — the belief this test measures now has a node of its own
