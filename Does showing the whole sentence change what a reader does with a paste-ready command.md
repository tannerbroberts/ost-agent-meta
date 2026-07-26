---
type: AssumptionTest
source: 'agent-ideation:2026-07-26-tenth-pass'
created: '2026-07-26'
evidence: assertion
---
#AssumptionTest #evidence/assertion

**The single assumption.** That a reader shown the full sentence actually *catches* the qualification the fragment hid — rather than skimming to the paste-ready line, as they did with the fragment.

**Proposed test.** Give readers from outside the building a `lanes` output containing one split declaration among several clean ones, in both renderings, and ask them to do what they would normally do. Measure whether the split one gets pasted.

**Lane: humans-required.** It measures a reader's behaviour, and the whole question is what a person does when not paying full attention — which is the one thing that cannot be simulated from inside.

**Pre-committed threshold.** Fragment rendering is expected to produce the wrong paste; the full-sentence rendering earns its keep only if **at least 4 of 5** readers decline to paste the split one, unprompted, with no instruction to look for a trap. **Three or fewer refutes it** — the extra text was decoration. Any reader who asks the interviewer what to look for is excluded, because that question is not available to a real operator at 2am.

**Why the bar is set where it is.** The failure this defends against happened to an attentive reader — this agent, reading its own tool's output while specifically auditing that tool. A fix that only helps readers already looking for the problem does not address the case that produced the node.

⚠️ Proposed only — the agent does not run tests or record results.
