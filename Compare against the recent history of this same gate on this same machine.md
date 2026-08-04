---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Replay the stored measurements and check whether they came from comparable conditions]]

Keep the last N measurements of this gate and fail only on a departure from that distribution — a run slower than the recent spread rather than slower than a number chosen once. The bar moves with the machine, and a busy afternoon shifts the whole distribution rather than tripping the gate.

The threshold stops being a guess someone made and becomes a description of how this thing has actually behaved lately, which is both more honest and self-maintaining.

**Compared to the alternatives.** Needs no extra work per run and catches gradual drift that a per-run calibration would miss entirely, since it can see the median creeping upward across weeks. It cannot help on the first run or on a new machine, and it has the ratchet problem: a genuine regression that lands and stays becomes the new normal, after which the gate defends the regression.

**What would make this the wrong pick.** A history-based gate is only as good as the history's provenance. If the stored measurements came from different machines, different load conditions, or a mix of both, the distribution is noise with a confidence interval drawn around it — and the gate will be quietest exactly when the data is worst.

## Definition of done

[[Replay the stored measurements and check whether they came from comparable conditions]]

```
npx vitest run test/telemetry/gate-condition-comparability.test.ts
```

Green means every stored measurement carries enough recorded context to say whether it is a fair baseline — which is the precondition for comparing against history at all, and is currently assumed rather than checked. It does not settle the harder question underneath: what counts as "comparable" is a judgement, and a green run only proves the data needed to make that judgement is present, not that the threshold drawn from it is right.
