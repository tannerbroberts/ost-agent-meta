---
type: Solution
status: unvalidated
source: 'agent-ideation:2026-08-20-unattended-sweep'
created: '2026-08-20'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The operator will accept a no-bar test entering the tree at write time if the census still catches it]]
[[The create-time bar check and the downstream threshold classifier disagree, so what one refuses the other would have accepted]]

**Variation dimension: automated vs manual — the bar check is deliberately moved off the automated write path.** `ost_create_node` stops refusing a no-spec instrument on the grounds that the threshold's number is spelled out rather than typed as digits. The test is written; the "does this test state a fixed bar?" question stays where the tree already answers it — the rollup's "N of M tests state no fixed bar" census and the human's `ost-agent verify` / `result` step, both of which read the threshold with judgement rather than a digit regex. The refusal that misled the session is removed rather than reworded.

**Compared to its siblings.** The only candidate that treats the observed refusal as a false positive rather than a badly phrased true one: "at least five of twenty" IS a fixed bar, and a regex that cannot see it is the defect. It gives up a guard at the cheapest moment (write time) in exchange for never sending a wrong-field refusal at all.

**What would make this the wrong pick.** The create-time check exists because this tree measured, on 2026-08-09, that most recorded reds were vacuous and many tests carried no bar; moving the check downstream means a no-bar test enters the tree and is caught only if somebody runs the census. Whether the operator will accept a weaker write-time guard for a cleaner refusal is a risk call that is theirs, not the code's.

⚠️ Unvalidated. Agent-ideated from one recorded session.

## Definition of done

"Ask the operator, with the 2026-08-09 vacuous-red count in hand, whether the write-time numeric-bar check may be relaxed"

No command, by design: this candidate trades a guard for a cleaner refusal, and whether that trade is acceptable is the operator's risk call — humans-required. A builder should not start this until that answer is recorded; a yes conditioned on some other write-time guard refutes it.

## Definition of done — the mechanical half (added 2026-08-22 unattended sweep)

The section above is right that the operator's risk call has no command. It is not the whole of what a builder needs, because it is asked on an unchecked premise: that the guard it proposes dropping is producing false refusals. That premise is code behaviour and a spec settles it.

"A word-bar threshold the create-time check refuses is classified bound by the census classifier"

```
npx vitest run test/eval/create-time-bar-parity.test.ts
```

Red today as a no-spec filing — the parity spec has not been written. It carries a bound bar, so it is a working permit rather than a vacuous red. What it settles is narrow: whether the two readers of a threshold string disagree. It says nothing about whether the trade this solution proposes is one the operator wants, which stays with the humans-required test above.
