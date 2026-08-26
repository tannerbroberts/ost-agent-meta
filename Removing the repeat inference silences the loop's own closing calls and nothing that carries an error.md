---
type: Assumption
created: '2026-08-26'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

**The belief, stated so it could be false:** deleting the `seenCalls` signature branch from `extractFriction` removes the two events the maintenance loop's closing step files on every pass, and removes nothing else that a reader would have wanted — because any repeat that mattered was accompanied by a result the host already flagged `is_error`, and that path is untouched.

**Risk category: feasibility.** It is a claim about what a specific edit to a specific function does to a specific input, and the repository can answer it.

**How it could turn out false.** A session can retry a call that did not error but returned something unusable — an empty result, a truthful "nothing to do" that the agent misread, a timeout the host reported as success. Those repeats carry real usability signal and no `is_error` anywhere, so they would go from filed to invisible. If the corpus holds many of them, this edit is not a filter but a deletion, and the sibling manifest candidate becomes the better answer.

**What it does not settle.** Nothing here touches whether the operator wants the quieter channel. A green on this belief proves the edit is surgical; it says nothing about whether a channel that files less is a channel anyone finds more useful, which is a desirability question for a person.
