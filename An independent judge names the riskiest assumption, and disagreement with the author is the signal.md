---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Have three independent judges nominate for ten solutions and see whether they agree with each other]]

A second party — a different model, a colleague, a reviewer who did not write the solution — reads it cold and names what it thinks would sink it. That nomination is recorded alongside the author's. Where the two agree, the gate has a well-supported target. Where they disagree, the gate says so and refuses to be satisfied by a test against only one of them.

Disagreement is the valuable output, not a problem to resolve. Two readers naming different fatal assumptions means the solution has at least two, and the author has seen one.

**Compared to the alternatives.** The only option that does not take the author's word for what is risky, which is the flaw in self-nomination and the reason a gate built on it can be comfortable. It costs a second reading per solution and it produces more work rather than less — every disagreement is another test to design. Testing the assumption that killed a comparable past idea is cheaper and looks backward instead.

**What would make this the wrong pick.** If the judge is another model with no independent grounding, it may produce plausible nominations with no more basis than the author's, and the appearance of independent corroboration is more dangerous than an openly self-assessed gate.

## Definition of done

[[Can riskiest-assumption-tested be judged mechanically]]

```
npx vitest run test/eval/riskiest-assumption-judge.test.ts
```

Green means a judge run independently of the author picks the same riskiest assumption as a committed labelled set often enough to be worth listening to. Note what green does *not* mean here, because this node is unusually easy to misread: the value in this solution is the *disagreement*, so a judge that agrees perfectly has proved it can be automated and simultaneously that it carries no signal. The command settles feasibility only, and the labelled set it scores against is itself somebody's opinion.
