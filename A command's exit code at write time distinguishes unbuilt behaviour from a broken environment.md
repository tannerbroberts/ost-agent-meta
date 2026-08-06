---
type: Assumption
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

**The belief, stated so it could be false.** Running the candidate command at write time yields a signal the guard can act on — a red exit means the behaviour is genuinely absent, not that the suite could not run.

**Kind.** Feasibility.

**How it could turn out false.** Red is the guard's accept condition, and almost everything that goes wrong is red: a missing dependency, a spec file that does not exist, a typo in the path, a machine under load. The tree already carries a whole bucket for this confusion — "A test that failed because the machine was busy looks exactly like one that failed because I broke something" — which is the same signal problem arriving at a different consumer. If red cannot be sorted into absent-behaviour and broken-environment, this guard accepts a command whose only red is a missing file, which is precisely the weak instrument the ruleset already warns against, and it will have done so with the authority of having executed something.

**Why it is the riskiest one here.** The solution's entire claim over its siblings is that it consults the repository instead of trusting a status field. If the repository's answer is uninterpretable, it has bought an execution capability — on a surface deliberately built without one — in exchange for a signal no better than the field it replaced.
