---
type: Solution
source: 'agent:ideation-2026-08-02'
created: '2026-08-02'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Would operators enable an update channel that can change an unattended agent]]

**Candidate (unvalidated, agent-ideated — one of three deliberately different mechanisms under this opportunity).**

**The mechanism.** The publisher announces; the instance listens. A running instance subscribes to an update channel, and when an update is announced it applies it at the next safe checkpoint — between passes, never mid-pass — so a change never lands on a half-finished write. This is the only one of the three where propagation begins on the publisher's side, which means an improvement can reach an instance the operator has not thought about in weeks.

**What it is good at.** It is the only candidate whose latency does not depend on the operator remembering anything, and the only one that could deliver an urgent fix to instances already in flight. Applying at a checkpoint rather than on demand is what separates it from the parent pain — [[Improving how the agent works means interrupting it]] is about the cost of changing a running agent, and a checkpoint is the one moment where that cost is near zero.

**Where it fails, stated plainly, and the failure is a trust failure rather than an engineering one.** It requires something outside the operator's machine to be able to change what the agent does there. This tree carries a whole branch about not being able to leave an agent running unattended without worrying, plus [[Fear the agent could take a destructive, irreversible action]] and [[Want proof no hijackable capability even exists]] (retired, but for the shape of the claim rather than the concern). A subscribed push channel is, precisely, a remote capability to alter an unattended agent's behaviour — it is hard to argue an operator should fear less about an agent that can be reprogrammed from elsewhere. It also cuts against the local, operator-owned positioning the free-distribution decision rests on. The honest read: this candidate buys the best propagation latency at the highest trust cost of the three, and if the trust cost is real the other two are strictly preferable.

**Compare against:** [[Resolve the newest published version at pass start and refuse to run silently on a stale one]] and [[The vault carries the agent it runs, upgraded by an ordinary git pull]] are both pull-shaped and both leave the operator's machine in control; this one is the only push-shaped option, and it should be judged on whether that control transfer is acceptable, not on whether it works.

**Assumption it rests on:** that an operator would enable a channel that lets someone else change an agent running unattended on their machine. Tested by [[Would operators enable an update channel that can change an unattended agent]].
