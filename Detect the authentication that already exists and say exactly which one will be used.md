---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[List what a detection probe would touch and have someone say whether they consent to each]]

At startup, look for the credentials the operator already has — the CLI that is logged in, the environment variable that is set, the config file that exists — and report what was found and which one will be used, before anything needs it. If none will serve, say so then, naming the ones that were found and why each was rejected.

The frustration this addresses is largely informational. Being asked for a credential is bearable; being asked while already authenticated, with no explanation of why the existing one will not do, is what makes it feel absurd.

**Compared to the alternatives.** Cheap, works everywhere, and needs no cooperation from any host. It does not actually let the existing credential be used — it only explains, and an operator who wanted to be unblocked has been given a clear account of why they are not. Borrowing the host's authority solves the problem; this makes the problem legible.

**What would make this the wrong pick.** Probing for credentials means touching places credentials live, and a tool that enumerates the operator's secrets to be helpful has done something they may not have wanted. What it looks at and what it reports both need care, and reporting a rejection reason can leak more than the rejection.
