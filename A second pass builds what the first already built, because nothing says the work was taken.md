---
type: Opportunity
source: 'agent-run:autonomous-loop-2026-08-07'
created: '2026-08-07'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[A pass claims the work item before it starts, and the claim outlives the session]]

**The need (operator's voice).** "I paid for eight hours of compute and got a commit I had to delete. Another run had already built the same thing six hours earlier, and nothing told either of them."

**Why this is its own need and not a restatement of its parent.** The parent, "Two agents sharing my vault can trample each other", holds two children and both are about *writes* colliding — a merge conflict committed into a source file, and two runs writing the vault with nothing arbitrating. This is not a write collision. The parent's own body says so, in the section recording the 2026-07-26 sighting: neither pass wrote the vault while building, git would have serialised them cleanly, and no vault lease would have helped. What collided was **the decision about what to work on**. Both passes read one briefing paragraph that names work and has no way to say the work has been taken, and both acted on it.

**What was observed, with times.** A loop iteration cloned the product repo clean at 00:47Z, read the standing briefing, and built the named feature: a migration, a derived experiment arm, a per-arm admin read, 28 new tests, four e2e tests green against real Chromium and real Postgres. It committed at 08:46Z. At 08:47Z the push was rejected — a commit pushed at 02:56Z by a different session was the same feature: same migration number, same column name, same hash function, same default-off knob. One 4-assertion test file was salvageable. Everything else was discarded.

**The part that makes this worth a node of its own.** The only detector in the system is `git push --ff-only`, it fires after all the cost has been paid, and it fired here only because the two implementations happened to touch overlapping files. **Two passes building non-overlapping duplicates of the same intent would both push cleanly and neither would ever know.** The observed cost is therefore a floor, not an estimate — it is what this failure costs when it is caught.

**Litmus — more than one way to address it?** Yes, and the three are genuinely different in kind: claim the work before starting so a second pass sees it is taken; scan for prior art at the start rather than discovering it at the push; or accept that collisions happen and shrink the window so a wasted pass costs minutes instead of hours.

**Why it was invisible until now.** This need has lived as prose inside its parent since 2026-07-26 and has never had a node. The parent reads as fully served — two children, three solutions under each — so every sweep that counts subtrees would mark it done. It surfaced only because a pass went looking for parents carrying needs their children do not hold, which the assumption "Most opportunities the sweep calls underserved are categories whose children are already served" had named as its own biggest unanswered question.

⚠️ Unvalidated. Distilled by an unattended pass from its parent's recorded observation. The rung is `assertion`, not `observed`: the collision itself was observed first-hand by the pass that wasted the work, but this node's source is that node's prose rather than a transcript recording, and the claim that operators other than this one would hit it is grounded in nothing at all — n=1, and the 1 is this building's own loop.
