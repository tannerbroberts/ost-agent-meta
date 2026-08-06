---
type: Assumption
source: 'agent-ideation:2026-08-06-unattended-sweep'
created: '2026-08-06'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Mutate the manifest server name and require the three prefix guards to go red]]

**The belief, stated so it could be false.** Mutating the source a self-derived guard reads from makes that guard follow the mutation and stay green, so mutation testing detects the "cannot fail" property this opportunity is about.

**Why it is the riskiest one.** It is the entire premise, and it has a known counter-case. If a mutation harness mutates the *product code* rather than the *shared source of truth*, a self-derived guard may well go red for an unrelated reason and be scored as healthy. The technique only detects the disease if the mutation is applied at the point the two sides share, and knowing where that is requires already knowing which guards are self-derived — which is the thing being detected. That circularity is worth surfacing before anyone funds a harness.

**What class this is.** Feasibility, and it has a ready-made oracle: the three prefix guards are known-defective and their defect is documented. A technique that cannot catch the case that motivated it should not be built.

**How it could come out false.** The mutation set is authored by the same party that authored the guards, so it can share their blind spot — this opportunity's own disease, one level up. If catching the prefix bug requires a mutation nobody would have thought to write, the technique works only where it was not needed.
