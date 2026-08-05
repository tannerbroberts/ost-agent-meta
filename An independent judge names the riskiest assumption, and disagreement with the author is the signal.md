---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Independent judges converge on the same riskiest assumption, so agreement means something]]

A second party — a different model, a colleague, a reviewer who did not write the solution — reads it cold and names what it thinks would sink it. That nomination is recorded alongside the author's. Where the two agree, the gate has a well-supported target. Where they disagree, the gate says so and refuses to be satisfied by a test against only one of them.

Disagreement is the valuable output, not a problem to resolve. Two readers naming different fatal assumptions means the solution has at least two, and the author has seen one.

**Compared to the alternatives.** The only option that does not take the author's word for what is risky, which is the flaw in self-nomination and the reason a gate built on it can be comfortable. It costs a second reading per solution and it produces more work rather than less — every disagreement is another test to design. Testing the assumption that killed a comparable past idea is cheaper and looks backward instead.

**What would make this the wrong pick.** If the judge is another model with no independent grounding, it may produce plausible nominations with no more basis than the author's, and the appearance of independent corroboration is more dangerous than an openly self-assessed gate.

## Definition of done

"Can riskiest-assumption-tested be judged mechanically"

```
npx vitest run test/eval/riskiest-assumption-judge.test.ts
```

Green means a judge run independently of the author picks the same riskiest assumption as a committed labelled set often enough to be worth listening to. Note what green does *not* mean here, because this node is unusually easy to misread: the value in this solution is the *disagreement*, so a judge that agrees perfectly has proved it can be automated and simultaneously that it carries no signal. The command settles feasibility only, and the labelled set it scores against is itself somebody's opinion.

## Definition of done — the second half

The section above instrumented the feasibility question for a single judge. This node's other test was still prose, which is why the solution kept reporting as un-instrumented: one runnable command under a solution with two tests leaves the second one unanswerable by anyone but a person finding the time.

"Have three independent judges nominate for ten solutions and see whether they agree with each other"

```
npx vitest run test/eval/judge-panel-agreement.test.ts
```

Red today because nothing runs a panel. `test/eval/riskiest-assumption-judge.test.ts` scores one judge against a labelled set; there is no code that puts several judges over the same solution and compares their nominations, so there is no agreement number to assert. Green means at least 2 of 3 judges name the same assumption on at least 6 of 10 solutions.

Read the two commands together, because they measure opposite things and this node is easy to misread. The first asks whether a judge can be automated at all. The second asks whether independent judges converge — and the value this solution claims is in the *disagreement*, so a panel that agrees on everything has proved it is mechanisable and simultaneously that it adds nothing to the author's own nomination. Neither command settles correctness: three judges sharing training can converge on the same wrong assumption, and no exit code here distinguishes that from convergence on the right one.

## History
- 2026-08-05 unlinked "Have three independent judges nominate for ten solutions and see whether they agree with each other" — moved under "Independent judges converge on the same riskiest assumption, so agreement means something" — the belief this test measures now has a node of its own
