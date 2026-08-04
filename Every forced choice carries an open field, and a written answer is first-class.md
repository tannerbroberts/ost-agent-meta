---
type: Solution
source: 'agent-ideated:2026-08-04-unattended-sweep-question-shape'
created: '2026-08-04'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

Keep the options — they are genuinely useful when the run has guessed right — but never make them the only way to reply. Every question the run asks carries an open field alongside the enumerated choices, and an answer written into that field is handled as an answer, not as a refusal. The operator who wants to say "neither, here is the actual distinction" says it once, in the same turn, and the run proceeds on it.

**Compared to the alternatives.** This is the smallest change of the three and the only one that leaves the run's existing question flow intact — the options still carry the common case at its current cost. It is also the weakest, because it fixes the *reply* channel without fixing the *asking*: the run still guesses at the frame, and the operator still has to do the work of correcting it, just in one turn rather than three. Cheap and partial.

**What would make this the wrong pick.** If the run cannot act on prose without a further round-trip, the open field is theatre: the operator writes their answer, the run fails to parse a decision out of it, and asks again — which is the observed failure with an extra step. The whole idea rests on the run being able to take a sentence as an instruction, which is exactly what the recorded rejections were.

⚠️ Unvalidated. Proposed by an unattended pass from one observed session.
