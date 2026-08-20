---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Error classes can be grouped so the counter fires on the second real repeat and changes behaviour]]

Errors are grouped into classes as they happen and counted. The first is answered as it is now. The second leads with the fact that it is the second, quotes what was said the first time, and states that the previous correction was not applied. By the fourth, the message is mostly about the pattern and barely about the command.

What changes is the caller's model of what is happening. Five separate messages about five separate commands read as five pieces of bad luck; one message saying "this is the fourth time in eleven minutes" reads as a habit, and only the second framing prompts a change of approach.

**Compared to the alternatives.** Cheap, general, and it needs no new design work per error class — it works for shell quoting, workflow parse errors, and anything else that recurs. It also arrives after the damage has begun, by construction, and it can only escalate wording rather than actually helping. A better affordance would have prevented all five.

**What would make this the wrong pick.** Everything depends on the grouping. Two zsh failures with different messages are the same class, and two identical messages from different causes are not — get that wrong and the counter either never fires or cries wolf, and a wolf-crying counter is quickly ignored.

## History
- 2026-08-05 unlinked "Apply the escalating message to the five-failure session and check where it would have fired" — moved under "Error classes can be grouped so the counter fires on the second real repeat and changes behaviour" — the belief this test measures now has a node of its own

## Definition of done

"Replay the five-failure and three-failure sessions through the class counter and require it to fire by the second occurrence in both"

```
npx vitest run test/loop/repeat-class-escalation.test.ts
```

Green means an in-session counter groups the five `(eval):1: == not found` failures of `TRANSCRIPT:a615eb46-cc50-41a9-a77f-931c0dc67db0` and the three of `TRANSCRIPT:b7aae32d-150a-462f-9027-cdf7af12badd` into one class each, answers the second occurrence with the count and the quoted first correction, and does not escalate across two genuinely different classes. It is red today because nothing in the repository counts repeats inside a live session: `src/loop/corrections.ts` keys on a guard's permitted form across finished sessions and drops non-zero exits on purpose. The spec does not exist yet either (no-spec red) — the builder's deliverable is the counter and the spec together.

It settles nothing about whether the message changes what a caller does next; that is "Show the escalated message to five fresh sessions facing the same failure and count which change approach", which needs people and is laned humans-required.
