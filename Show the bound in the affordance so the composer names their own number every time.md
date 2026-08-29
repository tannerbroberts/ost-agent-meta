---
type: Solution
source: 'agent-run:unattended-sweep-2026-08-29'
created: '2026-08-29'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[A bound can be spelled into the affordance in fewer characters than the margin it has to fit inside]]

**Variation dimension: who-does-the-work. Position taken: the person. The composer carries the bound, and the product's job is to stop hiding the place it goes.**

The bound is already an argument the shim accepts — `await '<condition>' [seconds-between-attempts] [give-up-seconds]`. Nobody passes it because nobody is ever shown it. `renderWaitAffordance()` in `src/loop/wait.ts` is the text that reaches a session at the exact moment it is refused, and all three of its example lines are the bare `await '<condition>'` form. This candidate changes those examples to carry an explicit interval and bound, so the form a composer copies is the form that states a number.

**Why put it on the person rather than infer it.** The bound is a claim about the operator's money and patience. The shim has no access to either, and a number inferred from the environment is a number nobody chose and nobody can be held to. Making it visible costs no plumbing, no new configuration surface and no second source of truth: the argument already exists and is already parsed.

**What it costs, and this is the objection that could kill it.** `src/loop/wait.ts` rests its entire case on expression cost — a permitted form longer to write than the blocked one is "a preference, not an affordance", and the module goes to some length to establish that the shim wins on all three recorded waiting cases. The suite pins those margins exactly: `expect(margins).toEqual([14, 25, 3])`. Appending ` 5 400` is six characters. It survives `ci-check` (14) and `started-task` (25) and **destroys `condition`, whose entire margin is 3**. On the module's own terms that turns the permitted form into a losing one for a third of the corpus. Any build here has to either accept losing that case, argue the margin was never the right measure, or find a shorter spelling than two trailing positionals.

**Against its siblings.** It is the only one of the three that adds no mechanism at all — no environment plumbing, no behaviour that differs between contexts, nothing new to keep correct as the harness changes. It is also the only one that makes the composer pay, in the exact currency the module says decides adoption.

Unvalidated, ideated by an unattended pass on 2026-08-29 against the assigned dimension. **Not blind:** this surface holds no grant to run independent parallel ideators, so all three candidates under this opportunity were composed in one context by one author — the condition the blind-ideation rule exists to prevent. Read them as one author's three answers and discount their apparent distinctness accordingly.
