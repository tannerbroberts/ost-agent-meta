---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

The operator hands the secret once, to a small local broker, and never to a run. A run asks the broker for a specific action against a specific target — push this branch, read this issue — and the broker performs it and returns the result. The run never sees the secret, and every request is logged with who asked, for what, and what came back.

This converts the credential from a thing a run must possess into a service a run may call. The operator's involvement moves from per-run to once, and what they are trusting is a written scope rather than an agent's judgement in the moment.

**Compared to the alternatives.** Strictly more capable than batching approvals, because the run never stops at all rather than stopping in one place. More expensive than short-lived tokens, since it needs a process that stays up and a policy language to express the scopes. Its real advantage over both is the audit log: it is the only one of the three that leaves a record of what the credential was actually used for.

**What would make this the wrong pick.** It concentrates every secret into one process on one machine. If that trade is unacceptable — and for some operators it plainly is — the scoped-token route gives most of the unblocking with none of the concentration.
