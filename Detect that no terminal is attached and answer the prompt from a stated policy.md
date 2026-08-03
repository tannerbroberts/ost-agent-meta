---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Sort the observed prompts into safe-to-default and must-stop, and see whether a rule separates them]]

The run notices it has no attached terminal and, for prompts it recognises, answers them itself from a policy the operator wrote and can read. Every such answer is recorded in the run's journal — the question, the answer given, and the policy line that supplied it — so the operator can see afterwards exactly what was decided on their behalf.

This is the only route that keeps the run going through a prompt rather than stopping at it or preventing it. The record is what makes that acceptable: an answer given silently is an agent acting on its own authority, and an answer given with a citation is an agent applying the operator's.

**Compared to the alternatives.** Uniquely, the run completes. It also handles prompts from tools that ignore non-interactive conventions, which is precisely where the other two options fail. The cost is the largest trust surface of the three, and a policy that does not cover the prompt leaves the run choosing between guessing and stopping.

**What would make this the wrong pick.** Answering prompts on the operator's behalf is a standing grant of authority, and the boundary of that grant is a human's to set, not a pass's to widen. Some prompts — a destructive overwrite, a force push — should stop the run no matter what any policy says.
