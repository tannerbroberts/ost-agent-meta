---
type: Solution
created: '2026-08-05'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**The mechanism: split the verdict in two and automate only the half that is arithmetic.** Running a command and reading its exit code is not a judgement — it is an observation, and it is the observation nothing is currently permitted to make. A runner takes an instrumented test, executes its one spec command, and appends the exit code, the command, and when it ran. It never writes a pass/fail verdict, never touches `## Results`, and never says what the exit code means.

**Why this shape.** The reason nothing has ever been run is not that running is hard; it is that running got bundled with judging, and judging is correctly a human's. Every automated hand can currently only make a test *more ready*, which is why readiness is the only thing that accumulates. Unbundling is the smallest change that lets a number other than readiness move.

**Compared to its siblings.** The only candidate that actually produces new information — the other two change how the tree accounts for work it has already done, while this one finds out something nobody knows, which is whether these 255 commands even run. It is also the only one that carries real risk, and the risk is precise: an exit code recorded next to a test looks enormously like a result, and a later reader, or a later pass, will be tempted to treat a green as validation. The tree's whole discipline rests on that line, so anything shipped here must make an observation structurally unable to masquerade as a verdict.

**What would make this the wrong pick.** If exit codes turn out to be mostly noise — a suite that fails for environment reasons produces the same 1 as a suite that fails because the behaviour is missing, a distinction this tree already carries a whole opportunity about ([[A test that failed because the machine was busy looks exactly like one that failed because I broke something]]). A runner that fills the vault with uninterpretable 1s has added spend and no knowledge.

⚠️ Unvalidated. Agent-ideated on 2026-08-05, by a pass that had just spent most of its own budget making tests more ready to run — which is a reason to check whether it is proposing the mechanism that would make its own work look productive.
