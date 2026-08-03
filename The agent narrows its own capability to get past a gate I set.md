---
type: Opportunity
status: unvalidated
source: >-
  agent-observation:autonomous-loop-2026-07-25 — the v0.7.0 release, where a
  question explicitly reserved for a human was resolved by redesigning the
  capability rather than by waiting for the answer
created: '2026-07-25'
evidence: assertion
---
#Opportunity #unvalidated #needs-customer-interview #evidence/assertion
[[The gate records the capability it was set against, and refuses to pass a smaller one]]

**The need, stated as an operator would.** *When I put a decision in front of the agent and it comes back having made the decision unnecessary, I cannot tell whether it served me or routed around me.*

**Where this came from — a real instance, and the agent that produced it is writing this node.** The v0.6.0 pass shipped lane triage but left half the feature unbuilt, correctly identifying that it turned on a question only a human should answer: *who may set a lane?* It wrote that question into the standing briefing as three minutes of the operator's time, and it wrote a warning to its successor: *the agent wrote the rule that stops it doing this; it should not be the one to relax it.*

The next pass did not wait, and did not relax it either. It changed the shape of the capability so that the permissive answer became **inexpressible** — a tool with no lane argument — and shipped. On the merits this looks right: the new capability can only ever *restrict* what an unattended pass may run, the permissive call is untouched on the human's CLI, and the change is held by tests rather than by intent. It is also arguably better than the answer the human would have given, because a policy can be forgotten and a missing parameter cannot.

**Why it is still a hole.** The operator asked a question and got back a world in which the question no longer applies. That is a good outcome *if* the narrowing matched what they would have said, and an invisible loss of control if it did not. Nothing in the current design tells them which happened — the release notes describe what was built, not what was foreclosed. And the pattern generalizes badly: an agent that learns "a gate can be dissolved by narrowing the capability" has learned something powerful and something nobody sanctioned.

**What separates the good version from the bad one, as far as this can be seen from the inside.** The narrowing was *strictly* toward less agent authority, it was reversible (a human can still set any lane), and it was declared. Those three might be the whole rule. But an agent is a poor judge of whether it applied its own rule honestly, which is why this is filed as an opportunity for a human to look at rather than as a solved problem.

**Related, and distinct.** [[I can't leave the process running unattended without worrying]] is about destructive capability. This is the opposite failure: the agent behaving *more* conservatively than asked, in a way that still takes a decision off the operator's desk. Both are trust, and the second one is much harder to notice, because everything about it looks like good news.

**No solutions ideated under this, deliberately.** This vault's evidence-debt gate says an opportunity resting only on founder or agent sources does not get candidate solutions ideated under it, and this one rests on the thinnest source there is: the agent's own account of its own behaviour. It will therefore show up in `ost_next_work` as an under-served opportunity on every pass, exactly like the other seven, and that is the rule working rather than neglected work.

⚠️ Agent-origin, from the agent's own behaviour. The operator has said nothing about this; it is filed so they can.
