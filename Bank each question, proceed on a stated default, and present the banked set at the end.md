---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The forks a run meets are mostly cheap to reverse, and the expensive ones are recognisable in advance]]

When a question arises, the run records it along with the answer it would give and why, takes that answer, and keeps going. At the end the operator sees all seven decisions together, each with what was assumed and what it would cost to reverse. Anything they disagree with is revisited then.

The trade is explicit: some work will be done on assumptions that turn out wrong and will have to be redone. Against that, the run finishes. For a session where all seven questions had a defensible default, that trade is heavily favourable.

**Compared to the alternatives.** Handles questions that only become visible mid-work, which is where deriving consequences up front fails completely. It also produces a much better record — what was assumed, and what reversing costs — than any answer given in the moment. It is the option that requires the most trust, since the operator is reviewing decisions already acted on rather than making them.

**What would make this the wrong pick.** Not every fork is cheap to reverse. Deleting a command, deprecating a published package, choosing where work happens — several of the seven in the evidence were structural, and a run that took a default on those and was wrong has destroyed more than it saved. Which classes may be defaulted is a human's standing decision, not the run's.

## Definition of done

[[Sort the seven questions by reversal cost and count how many were safe to default]]

`npx vitest run test/loop/question-banking.test.ts`

The spec asserts the guard that separates this from the version that destroys more than it saves: a question in a class the operator has **not** marked defaultable blocks instead of defaulting, and every banked decision records both the assumption taken and what reversing it would cost. The node is explicit that "which classes may be defaulted is a human's standing decision, not the run's", so the policy being human-set and consulted is the load-bearing property, not the banking itself. Red today because nothing banks questions — a run either asks and stops or does not ask at all.

**What a green here does not settle.** Whether the defaults were any good. The node names the real hazard concretely — deleting a command, deprecating a published package, choosing where work happens were among the seven in the evidence, and a run that defaulted wrongly on those has already done the damage by the time the operator reads the bank. A spec can prove the structural questions were refused a default; it cannot price a reversal, and it cannot tell whether the operator will actually revisit the ones they disagree with rather than accepting a finished run. This is also the option the node says "requires the most trust", and trust is not a suite's output.

## History
- 2026-08-05 unlinked [[Sort the seven questions by reversal cost and count how many were safe to default]] — moved under [[The forks a run meets are mostly cheap to reverse, and the expensive ones are recognisable in advance]] — the belief this test measures now has a node of its own
