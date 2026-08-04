---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Load the machine deliberately and check that the calibration ratio holds while the raw number does not]]

The gate stops measuring milliseconds and starts measuring a ratio. Immediately before the real measurement, the same run executes a small fixed workload of known cost — the calibration — on the same machine under the same load. The gate compares the measurement to the calibration. A machine that is twice as busy makes both numbers twice as large and the ratio unchanged.

This is what makes the gate a statement about the code rather than about the afternoon it ran in.

**Compared to the alternatives.** Handles the exact failure named in the opportunity and needs no history, so it works on the first run and on a machine never seen before. It costs a little time on every run to produce the calibration, and it depends on the calibration workload degrading the same way the real one does under load — which is true for CPU-bound work and much less true once disk or network is involved.

**What would make this the wrong pick.** If the thing being measured and the calibration respond differently to contention, the ratio drifts for reasons that have nothing to do with the code, and the gate is now failing unpredictably instead of predictably. That would be a worse position than the absolute number, which is at least wrong in a direction people understand.

## Definition of done

[[Load the machine deliberately and check that the calibration ratio holds while the raw number does not]]

```
npx vitest run test/eval/calibration-ratio-stability.test.ts
```

Green means that with the code unchanged across four induced load levels, the raw measurement spreads by more than 50% while the ratio against the calibration run spreads by under 10%. It is red today because no calibration run exists and the gate has no ratio to compute.

**Both clauses are load-bearing and the first is the one people skip.** A ratio that stays flat is only evidence of anything if the raw number moved — a quiet machine produces a stable ratio and a stable raw number alike, and asserting only the ratio would pass on a run that never induced any load at all. The 50% clause is what makes the 10% clause mean something.

**A tension worth naming, because this vault already holds the other side of it.** This command is itself a timed check, and [[Run the timed check under isolation, or do not let it fail the build at all]] argues that timed checks running where isolation cannot be guaranteed should not be allowed to fail a build. That applies here: this spec deliberately contends for the machine, so it belongs in an isolated lane rather than in the ordinary suite, and running it on shared CI would produce exactly the ambiguous red that node is about.

**What green does NOT settle.** One machine and one kind of induced load. The assumption is that the calibration workload degrades the way the real one does, and that holds for CPU-bound work and much less well once disk or network is involved — contention from disk behaves differently, and a laptop under thermal throttling differently again. Green on CPU contention is not green on the class.
