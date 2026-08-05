---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Safe-to-default prompts separate from must-stop ones by a rule someone can write down]]

The run notices it has no attached terminal and, for prompts it recognises, answers them itself from a policy the operator wrote and can read. Every such answer is recorded in the run's journal — the question, the answer given, and the policy line that supplied it — so the operator can see afterwards exactly what was decided on their behalf.

This is the only route that keeps the run going through a prompt rather than stopping at it or preventing it. The record is what makes that acceptable: an answer given silently is an agent acting on its own authority, and an answer given with a citation is an agent applying the operator's.

**Compared to the alternatives.** Uniquely, the run completes. It also handles prompts from tools that ignore non-interactive conventions, which is precisely where the other two options fail. The cost is the largest trust surface of the three, and a policy that does not cover the prompt leaves the run choosing between guessing and stopping.

**What would make this the wrong pick.** Answering prompts on the operator's behalf is a standing grant of authority, and the boundary of that grant is a human's to set, not a pass's to widen. Some prompts — a destructive overwrite, a force push — should stop the run no matter what any policy says.

## Definition of done

"Sort the observed prompts into safe-to-default and must-stop, and see whether a rule separates them"

`npx vitest run test/runner/no-tty-policy-answer.test.ts`

The spec asserts the boundary that makes this acceptable rather than reckless. With no terminal attached: a recognised prompt is answered from the written policy and journalled with the question, the answer given, and the policy line that supplied it — the citation is what separates an agent applying the operator's authority from one acting on its own. A prompt outside the policy stops the run rather than being guessed at, and the must-stop classes the node names — a destructive overwrite, a force push — stop it whatever any policy says. Red today because nothing detects the absent terminal or holds a prompt policy.

**What a green here does not settle.** Whether the policy's boundary is in the right place. The node states plainly that the grant of authority is a human's to set and not a pass's to widen, and a spec can only enforce the line someone drew — it cannot tell whether that line was drawn well, and it is the largest trust surface of the three siblings. Sorting the observed prompts into safe-to-default and must-stop is the humans-required judgement that produces the policy this spec would then defend.

## History
- 2026-08-05 unlinked "Sort the observed prompts into safe-to-default and must-stop, and see whether a rule separates them" — moved under "Safe-to-default prompts separate from must-stop ones by a rule someone can write down" — the belief this test measures now has a node of its own
