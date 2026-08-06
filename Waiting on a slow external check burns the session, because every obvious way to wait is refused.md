---
type: Opportunity
source: 'TRANSCRIPT:081b644b-e90a-472e-9b3d-15562a030a94'
created: '2026-08-06'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed

Observed in two separate sessions: `sleep 45 && gh pr checks 54`, `sleep 30 && gh pr checks 55`, `sleep 45 && gh pr checks 17` — each blocked with the same guidance about `until`-loops and background runs, each rediscovered from scratch. The same sessions carry three identical `TaskOutput` re-polls of the same task id, which is the same need expressed through a channel that does not refuse it.

The need is not for the guard to be removed — the refusal is correct. It is that waiting for something slow is a routine, recurring act with no first-class way to express it, so the operator's agent pays the discovery cost again in every session that has to wait for CI.
