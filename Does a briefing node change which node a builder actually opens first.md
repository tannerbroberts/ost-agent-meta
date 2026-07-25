---
type: AssumptionTest
status: unvalidated
source: '>-'
created: '2026-07-25'
---
#AssumptionTest #ported-from-ost-agent-vault

**Assumption under test (desirability, not feasibility).** That the reason builders don't act on this tree is that the prioritization is *hard to find* — not that it is unconvincing, or that builders would rather decide for themselves. Building the node is trivial; this assumption is the entire risk.

**Two live readers are available right now, which is unusual and should be used.** This project is running a builder agent that reads this OST directly and chooses what to build from it, and a second OST-Agent instance is maintaining the tetrix vault. Both are real readers of real trees. This can be tested in days, against subjects that already exist, without recruiting anyone — a luxury almost nothing else in this tree has.

**Proposed test — the cheapest version, and deliberately not the impressive one.** Do not build the feature first. Take the briefing the tetrix agent already wrote (root Outcome, commit `2328e61`) — the content is good and already exists — and put a copy at its own address. Then observe what a builder reading each vault picks up and, more importantly, what it says its reasoning was. Compare against builders reading the tree as it stands.

**Pre-commit the threshold.** The briefing works if readers converge on the build the briefing names *and cite the briefing's reasoning* when explaining why. It fails if they converge on it without reading it — which would mean the tree already communicated the priority and the briefing is redundant. It also fails if readers find the briefing, disagree with it, and pick something else: that is not a discovery problem, it is a persuasion problem, and no amount of relocating text will fix it.

**The most likely way this test misleads.** A briefing written by an agent, read by an agent, in a vault built by an agent, is a closed loop that will happily agree with itself — and this whole tree already carries the standing caveat that nothing in it is human-sourced. Agent readers establish that the *mechanism* works; they cannot establish that a human on Monday morning would act on it. Treat a pass here as necessary and not sufficient, and say so in the result rather than letting a green light travel further than it should.

**Note the deliberate bias check.** The tetrix agent warned that an agent will steer toward work it can do alone. This test is exactly such work — cheap, self-contained, no humans required. That is a reason to run it, and also a reason to weight its result down.

⚠️ Proposed only — the agent does not run tests.
