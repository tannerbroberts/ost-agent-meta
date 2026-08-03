---
type: Solution
source: 'agent-ideated:2026-08-03-unattended-sweep-unattended-decisions'
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**Where authority sits: unchanged.** The human still decides everything they decide today. What changes is that deciding stops being on the critical path of the run.

When a pass reaches a fork it cannot take, it writes the question down — the question, the options it can see, the option it would pick and why, and the list of work that is downstream of the answer — and then keeps going on everything that is *not* downstream. The run ends with a completed body of independent work and a queue of banked questions, each one costed by how much work it is holding up. The human answers a batch; the next pass drains the queue first.

**How it compares to its siblings.** This is the conservative candidate: it is the only one of the three that cannot produce a decision the human did not make, so it is the only one that is safe to turn on before any trust has been established. It buys the least, too — the decision-heavy work still waits, and if most of a run's remaining work turns out to depend on the pending answer, a queue converts a hard stop into a nearly-as-hard stop with better paperwork.

**Its chief risk, which is not the obvious one.** The obvious risk is that the queue goes unanswered; that is real but it is the same risk this vault already carries and already has a row for. The load-bearing risk is *dependency judgement*: the agent decides for itself what is independent of an unanswered question, and it decides that at exactly the moment it has demonstrated it does not know the answer. Work built on a wrong independence call is worse than a stall, because it looks finished.

**Where it fits what this vault already has.** `ost_next_work` already reports `outstandingAsks` aged by how long they have gone unanswered, so the queue's read side partly exists; what does not exist is the write side — a pass has no way to bank a question, and no way to record what that question is blocking.
