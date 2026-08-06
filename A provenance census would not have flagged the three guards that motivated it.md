---
type: Assumption
source: 'agent-ideation:2026-08-06-unattended-sweep'
created: '2026-08-06'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

**The belief, stated so it could be false.** A syntactic provenance trace catches enough of the self-derivation pattern to be worth running, including the three prefix guards that exposed the problem.

**Why it is the riskiest one.** The solution's own body concedes this is probably wrong — the three guards derived the prefix *independently*, so a census keyed on shared symbols may score them as three unrelated checks. That concession is honest and it is also exactly what should be tested rather than assumed, because the answer determines whether this is a cheap useful measurement or a number that reassures without covering anything.

**What class this is.** Feasibility, with a built-in oracle. The three defective guards are known and documented, which makes this one of the rare cases where a detector can be scored against ground truth on the day it is written.

**How it could come out false — and why that is still worth knowing.** If the census misses all three, it is not thereby useless: it would still size the population of *syntactically* self-derived checks, which nobody has counted. But it would have to be re-described as measuring a related population rather than as a response to this opportunity, and it should not be built as though it answers the question that prompted it.
