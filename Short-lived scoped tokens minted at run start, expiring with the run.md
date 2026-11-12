---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[A run's credential needs are predictable enough to scope in advance]]

Before dispatching a run, the operator mints a token narrowed to what that run is expected to need and set to expire when the run should have finished. The run carries it and never asks for anything else. What the operator approves is a bounded grant, not an open-ended one, and the bound is enforced by the issuer rather than by the run's restraint.

**Compared to the alternatives.** Far less machinery than a broker — no long-lived process, no policy language, nothing to keep up — and it never concentrates every secret in one place. What it gives up is the audit trail and the ability to handle anything unforeseen: a run that discovers mid-flight that it needs one more scope is blocked exactly as it is today, which is the failure this whole opportunity is about. Against batched approvals, it front-loads the human's involvement instead of interrupting them later.

**What would make this the wrong pick.** It requires predicting the run's needs in advance. If runs routinely discover work the operator did not anticipate — and an autonomous discovery pass is close to the worst case for that — the scopes will be either too narrow to help or so wide that they are the original credential wearing an expiry date.

## History
- 2026-08-05 unlinked "Replay ten past runs and count how many needed a scope nobody would have predicted" — moved under "A run's credential needs are predictable enough to scope in advance" — the belief this test measures now has a node of its own

## Issues
- 2026-11-12 2026-11-12 unattended sweep: examined for a missing instrument and deliberately left without one. The one belief beneath it, "A run's credential needs are predictable enough to scope in advance", is tested by "Replay ten past runs and count how many needed a scope nobody would have predicted" — a hand replay in which a person judges what was predictable. No exit code encodes that judgement, and nothing about token minting lives in the product repository for a spec to be red against. Judged from this node's body and the test's title; the test's body was not read. What a human should do: `ost-agent lane --set` on the test (`ost_flag_humans_required` is withheld on this surface). Not a skipped step; no instrument, lane, rung or status changed.
