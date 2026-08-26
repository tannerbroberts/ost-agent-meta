---
type: Assumption
created: '2026-08-10'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion
[[Seed five axiom asks into the standing queue and count answers within a week]]

**Risk category: viability.** Lazy elicitation trades the up-front session for a stream of small asks. The belief is that the stream is thin enough — a few asks per week, each answerable in a minute — that the operator actually clears it. It could be false: if early theory work fans out (every derivation touching a new corner needs a new axiom), the queue floods, asks age unanswered, and derivations block indefinitely — reproducing exactly the founder's original frustration, an evidence regime the operator cannot feed. The vault's own outstanding-asks machinery shows asks can sit with no answer on record.

## Adjacent evidence already on this vault, counted (2026-08-26)

This assumption's closing line — "the vault's own outstanding-asks machinery shows asks can sit with no answer on record" — is true and understates what the machinery now shows. The numbers, read off this sweep's `ost_next_work` and the tree rollup:

- **454 assumption tests sit in a needs-a-person lane. Zero have a recorded result.** Not zero this week — zero ever. The rollup reports `tested 0` for all 37 buckets without exception.
- **50 of those are on the standing ask queue, and all 50 carry `askedAt: null`** — they predate ask tracking, so the queue cannot say how long any of them has waited.
- **0 tests are in the `runnable` (compute-only) lane.** Every outstanding question on this tree is waiting on a person.

**Why this is evidence here and not proof.** It is the wrong content and the right mechanism. These are assumption-test asks, not axiom asks: they are longer to answer than the one-minute accept-or-reject this candidate posits, and an operator who ignores a request to run a usability study has not thereby declined to ratify an axiom. So the answer rate above is not this assumption's answer rate. What transfers is the *channel* — one standing queue, cleared at one human's cadence, which is exactly the delivery mechanism the lazy-elicitation candidate proposes to add load to. On the only channel of that shape this vault has ever run, the observed clearance is 0 of 454 over roughly a month.

**What it changes for the seeded test.** The test beneath this node — "Seed five axiom asks into the standing queue and count answers within a week" — is still the right experiment and is still worth running, but it should be read as measuring whether *axiom* asks behave differently from everything else already in that queue, not whether the queue works. If five seeded asks are answered within a week while 50 older ones stay untouched, that difference is the finding, and the test should record the older queue's state at the same moment so the comparison exists. If they are not answered, this candidate's sharpest risk is realised on its first trial.

**The bound.** Zero recorded results is a fact about the record, not about the operator: a result answered in conversation and never entered with `ost-agent result` is invisible here and would look identical. That gap is itself already a node on this tree — "Tests get written and instrumented all day, and not one of them has ever been run" — and whoever runs the seeded test should settle which of the two readings holds, because they point at different products.

_Source: this pass's own `ost_next_work` response and the tree rollup it was given. First-party observation of the vault's state. No test was run and no result is recorded._
