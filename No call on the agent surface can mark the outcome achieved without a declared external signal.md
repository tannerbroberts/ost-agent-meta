---
type: Assumption
created: '2026-08-07'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

**The belief, stated so it could be false.** The circularity this solution closes can be closed by construction rather than by discipline: the outcome can carry a declared external signal, and every write path available to compute can refuse to record the outcome as met while that signal is undeclared or unmet — the same way `validated` is absent from `ost_set_status` and promotion is a human's CLI call.

It could be false. There may be no single chokepoint: if "the outcome was met" can be expressed as ordinary prose appended to the root, no refusal can catch it, and the guarantee degrades into a convention the agent is asked to honour. A declared signal may also have nowhere to live that compute cannot itself write — a signal the agent can declare is a gate the agent can open.

**Why this assumption exists as a second belief under this solution.** The solution's other assumption — "Teams can define an external signal that decides whether their outcome was met" — is about whether real teams can and will name such a signal, which is a question for people and stays with them. That belief is why this node was uninstrumentable, and it is a different claim from whether the product can hold the gate at all. A team that cannot name a signal makes this solution useless; a product that cannot enforce one makes it a promise.

**What settling this does not settle.** A green refusal proves compute cannot open the gate. It says nothing about whether any team defines a signal worth gating on, whether the signal they define measures what they think, or whether a human with CLI access uses the escape hatch every week. Those are the three ways this solution fails in the field and none of them has an exit code.

⚠️ Unvalidated. Authored by an unattended pass with no repository sight, so "this does not exist today" is inferred from the tree's own records rather than verified against the code.
