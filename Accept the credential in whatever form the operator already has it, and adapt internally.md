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
