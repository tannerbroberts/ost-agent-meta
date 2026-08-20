---
type: Solution
status: unvalidated
source: 'agent-ideation:2026-08-20-unattended-sweep'
created: '2026-08-20'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The operator will accept a no-bar test entering the tree at write time if the census still catches it]]

**Variation dimension: automated vs manual — the bar check is deliberately moved off the automated write path.** `ost_create_node` stops refusing a no-spec instrument on the grounds that the threshold's number is spelled out rather than typed as digits. The test is written; the "does this test state a fixed bar?" question stays where the tree already answers it — the rollup's "N of M tests state no fixed bar" census and the human's `ost-agent verify` / `result` step, both of which read the threshold with judgement rather than a digit regex. The refusal that misled the session is removed rather than reworded.

**Compared to its siblings.** The only candidate that treats the observed refusal as a false positive rather than a badly phrased true one: "at least five of twenty" IS a fixed bar, and a regex that cannot see it is the defect. It gives up a guard at the cheapest moment (write time) in exchange for never sending a wrong-field refusal at all.

**What would make this the wrong pick.** The create-time check exists because this tree measured, on 2026-08-09, that most recorded reds were vacuous and many tests carried no bar; moving the check downstream means a no-bar test enters the tree and is caught only if somebody runs the census. Whether the operator will accept a weaker write-time guard for a cleaner refusal is a risk call that is theirs, not the code's.

⚠️ Unvalidated. Agent-ideated from one recorded session.
