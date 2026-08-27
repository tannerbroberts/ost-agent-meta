---
type: AssumptionTest
source: 'agent-run:unattended-sweep-2026-08-27'
created: '2026-08-27'
evidence: assertion
lane: humans-required
threshold: at least 3 distinct operator-authored changes to the key over 8 weeks
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: humans-required.**

`discovery.target` is already in the vault and is already exactly this shape: human-set, no tool can write it, and it steers what a firing is shown. So the bet this test needs to settle has been running in production for weeks without anyone framing it as an experiment. Read `ost.config.yaml`'s history in the vault's git log, count the commits in which a person changed that key, and discount any written by a firing.

**Why the bar is three and not one.** One change is the setting; the assumption is about *re-*setting. Three distinct operator-authored changes over eight weeks is the weakest pattern that distinguishes a control someone steers from a control someone configured once.

**What makes this cheap.** Nothing has to be built, nobody has to be recruited, and no future has to be waited for — the behaviour is already on disk. That is the argument for running this before either sibling candidate is built, because a refuted verdict here removes a candidate from the consideration set for the price of reading a log.

**Why it is not compute-only despite being a git command.** The count is mechanical; the judgement is not. Deciding which commits were the operator steering rather than a firing writing, and whether an eight-week window during which this vault's other 51 asks went unanswered is representative of how this operator would treat a control they actually wanted, is a reading of a person's conduct. Handing that to an unattended firing would let the pass that authored the candidate also grade its own bet.

**What a verdict here does not settle.** Only follow-through, and only this operator's. It says nothing about whether the window mechanism is feasible, nothing about whether a different operator would behave differently, and nothing about the rate or quality of the coverage a moved window would produce.

A person outside the building is the measurement here: The operator is the measurement: this counts whether a specific person, unprompted and over weeks, kept steering a hand-held config key. A firing cannot observe its own operator's future behaviour, and asking them to predict it would collect a stated intention, which is the cheap answer this test exists to avoid.
