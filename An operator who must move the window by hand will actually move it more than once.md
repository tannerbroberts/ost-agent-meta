---
type: Assumption
source: 'agent-run:unattended-sweep-2026-08-27'
created: '2026-08-27'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion
[[Count how many times the operator amends discovery.target over eight weeks of git history]]

**The belief, stated so it could be false.** An operator handed a config key that selects which slice of the backlog their firings are shown will amend it repeatedly over the life of a tree, rather than setting it once and leaving it.

**Risk category: desirability, shading into usability.** It is a claim about what a person will do with a control, and no amount of reading the code settles it.

**Why it is the riskiest thing this candidate rests on.** The entire coverage benefit is downstream of the amending. Set once and forgotten, this candidate is bit-for-bit today's defect with a new owner — the same 25 items every firing, forever, now by the operator's own configuration. So the candidate is not "a way to advance the window"; it is a bet that a person will advance it, and the bet is the whole thing.

**Prior evidence that cuts against it, which is why the bet is worth naming rather than assuming.** This tree carries 51 outstanding asks, every one of them a question put to the operator with a ready-made command that would answer it, and all 51 have gone unanswered long enough that none carries a recorded age. It also carries a standing hold on a sibling branch that nine consecutive firings have logged and nobody has resolved. The observed base rate for "the operator will perform a small recurring maintenance act on this vault" is, on the record available, low. That is not proof — none of those asks is this ask, and an operator may well treat steering their own attention differently from answering a queue of test verdicts — but a candidate whose value rests entirely on operator follow-through should be read against it.

**What settles it.** Watching, not asking. A stated intention to amend a config key is close to free to give and is not the measurement.

**What a supported verdict would still leave open.** Nothing about whether the window mechanism works, which is a separate feasibility question this node does not touch, and nothing about the two sibling candidates, whose value does not depend on anybody doing anything.
