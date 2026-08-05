---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A run's credential needs are predictable enough to scope in advance]]

Before dispatching a run, the operator mints a token narrowed to what that run is expected to need and set to expire when the run should have finished. The run carries it and never asks for anything else. What the operator approves is a bounded grant, not an open-ended one, and the bound is enforced by the issuer rather than by the run's restraint.

**Compared to the alternatives.** Far less machinery than a broker — no long-lived process, no policy language, nothing to keep up — and it never concentrates every secret in one place. What it gives up is the audit trail and the ability to handle anything unforeseen: a run that discovers mid-flight that it needs one more scope is blocked exactly as it is today, which is the failure this whole opportunity is about. Against batched approvals, it front-loads the human's involvement instead of interrupting them later.

**What would make this the wrong pick.** It requires predicting the run's needs in advance. If runs routinely discover work the operator did not anticipate — and an autonomous discovery pass is close to the worst case for that — the scopes will be either too narrow to help or so wide that they are the original credential wearing an expiry date.

## History
- 2026-08-05 unlinked [[Replay ten past runs and count how many needed a scope nobody would have predicted]] — moved under [[A run's credential needs are predictable enough to scope in advance]] — the belief this test measures now has a node of its own
