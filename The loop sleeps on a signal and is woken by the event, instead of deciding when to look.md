---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Census every source of new work in this vault and check which can be watched as an event]]

The loop does not choose an interval at all. It finishes its work, registers interest in the things that could give it more — a file landing in a watched folder, a check completing, a human recording a result — and blocks. Something arriving wakes it. Nothing arriving costs nothing.

This removes the question the opportunity is really about. A loop that must decide when to run next is forced to guess whether work exists, and guessing wrong in one direction wastes money while guessing wrong in the other leaves the tree stale. A woken loop never guesses.

**Compared to the alternatives.** Strictly better than a stop predicate at the moment of stopping, because it also answers when to start — but it needs every source of new work to be observable as an event, and some are not. Against a spend ceiling, this addresses the cause rather than capping the symptom, and so it does nothing at all about a loop that is genuinely busy doing worthless work.

**What would make this the wrong pick.** If the meaningful triggers cannot all be watched, a woken loop will sleep through real work and look perfectly healthy doing it — a quieter failure than idling, and a harder one to notice.
