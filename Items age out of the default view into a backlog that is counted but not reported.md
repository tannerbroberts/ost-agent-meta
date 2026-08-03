---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Replay past sweeps to see what an ageing rule would have moved to the backlog]]

An item reported outstanding for N consecutive passes with nothing done about it moves into a backlog. It is still counted, still queryable, still there — but the sweep stops leading with it, and `done` is computed over the active list. Ageing does the sorting, so nobody has to decide anything.

The argument is that repetition is itself information. An item that has survived twenty passes untouched is telling you something about its actionability that no amount of re-reporting will change, and the only party who can act on that fact is a human looking at the backlog deliberately.

**Compared to the alternatives.** Requires no permission model, no new verb, and no judgement from any pass — it is a rule over the tree's own history, and it cannot be gamed by an agent because no agent invokes it. It is also the crudest: it cannot distinguish an item nobody may act on from one everybody has been avoiding, and those want opposite responses.

**What would make this the wrong pick.** Ageing rewards neglect. The surest way to get something out of the outstanding list becomes ignoring it for long enough, and the items most likely to be ignored are the difficult ones. A backlog assembled that way is a list of exactly the work that most needed attention.
