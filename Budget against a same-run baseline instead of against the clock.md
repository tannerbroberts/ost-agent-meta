---
type: Solution
source: 'agent-ideation:2026-08-02-maintenance-pass'
created: '2026-08-02'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A same-run baseline rises with load in step with the thing it is normalising]]

**The idea.** The test measures a trivial reference operation in the same process, at the same moment, under the same contention, and asserts a *ratio* — `ost_next_work` must complete within N times the baseline — instead of an absolute 2000ms. When the box is loaded, both numbers rise together and the ratio holds. When the code regresses, the ratio moves and the test goes red.

**Why it addresses the need.** It attacks the actual cause named in both filings: zero tolerance for suite-level CPU contention. Contention is a common-mode effect on every timing in the process, and a ratio is the standard way to cancel a common-mode effect. Both observed failures — 2004ms and 2280ms against 2000ms, each passing at 18077ms of margin in isolation — are exactly the shape a ratio would have absorbed.

**How it differs from its siblings.** It keeps time as the thing being measured, which matters if the operator genuinely cares about wall-clock. "Assert on work units instead of milliseconds" gives up on time entirely and measures something more stable but less relevant. "Re-run once and report the disagreement rather than the first result" accepts the flake and changes what is done about it.

**Where it fails.** The baseline operation has to be genuinely representative, and choosing it is guesswork — a baseline that is CPU-bound will not cancel contention for work that is I/O-bound, and this operation reads a whole vault off disk. If the baseline is wrong the test becomes noisier rather than quieter, and worse, its failures become harder to interpret than the honest absolute number was. There is also a real chance the ratio drifts slowly as the vault grows and nobody notices, which trades a loud wrong signal for a quiet absent one.

**Cost.** Small: one helper and a changed assertion.

⚠️ Unvalidated. Agent-ideated from two observed flakes, 2026-08-02.

## Definition of done

"Replay both flakes and one planted regression against the ratio"

```
npx vitest run test/telemetry/same-run-baseline-ratio.test.ts
```

Green means the two recorded flakes pass and the planted regression fails — the discrimination an absolute clock threshold cannot make, and the whole reason this candidate exists. It does not settle the ratio's behaviour on a machine whose *baseline* is itself degraded, which is the case a same-run comparison is least able to see.

## History
- 2026-08-05 unlinked "Replay both flakes and one planted regression against the ratio" — moved under "A same-run baseline rises with load in step with the thing it is normalising" — the belief this test measures now has a node of its own
