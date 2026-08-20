---
type: Assumption
source: 'agent-ideation:2026-08-20-unattended-sweep'
created: '2026-08-20'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Create a test with a digit-less threshold on a no-spec instrument and require the refusal to name the threshold]]

**Kind: feasibility.** The belief is that the check which fired ("cannot carry that instrument") is evaluated at a point where the failing field is known, so the message can be made to name `threshold` — and the passing form — with a wording change alone. It would be false if the check is a single combined predicate over instrument-and-threshold that has already lost which half failed by the time it throws, in which case the message cannot be honest without the check being split first.

Stated so it can fail: a refusal for a digit-less threshold on a no-spec instrument names `threshold` in its text and does not name the spec path as the cause.
