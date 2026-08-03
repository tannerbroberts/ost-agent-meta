---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Apply the escalating message to the five-failure session and check where it would have fired]]

Errors are grouped into classes as they happen and counted. The first is answered as it is now. The second leads with the fact that it is the second, quotes what was said the first time, and states that the previous correction was not applied. By the fourth, the message is mostly about the pattern and barely about the command.

What changes is the caller's model of what is happening. Five separate messages about five separate commands read as five pieces of bad luck; one message saying "this is the fourth time in eleven minutes" reads as a habit, and only the second framing prompts a change of approach.

**Compared to the alternatives.** Cheap, general, and it needs no new design work per error class — it works for shell quoting, workflow parse errors, and anything else that recurs. It also arrives after the damage has begun, by construction, and it can only escalate wording rather than actually helping. A better affordance would have prevented all five.

**What would make this the wrong pick.** Everything depends on the grouping. Two zsh failures with different messages are the same class, and two identical messages from different causes are not — get that wrong and the counter either never fires or cries wolf, and a wolf-crying counter is quickly ignored.
