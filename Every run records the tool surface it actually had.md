---
type: Solution
source: 'agent-ideation:2026-08-02-maintenance-pass'
created: '2026-08-02'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Hand a reader five run records and ask which passes did their job]]
[[The run record names the tools it had and the ones it expected and did not get]]

**The idea.** Every pass writes into its run record the tool surface it observed at start: which tools were present, which were expected and absent, and the environment facts that explain the difference. Nothing is blocked and nothing halts. The record simply stops being silent about the variable that decides what a pass could do.

**Why it addresses the need.** The four filings converged on the right cause only after three wrong ones, over five passes and roughly a day. Every wrong diagnosis was an inference from the *shape of the failure* because there was no record of the capability itself. A recorded surface makes the diagnosis a lookup instead of an inference, and — more useful — makes it visible to a human reading a week of runs at once, which is when a per-surface pattern becomes obvious and a single run's is not.

**How it differs from its siblings.** [[A run declares the tools it needs and halts loudly when they are absent]] prevents the wasted pass; this one does not prevent anything. It is strictly weaker and strictly cheaper, and it is the only one of the three that is useful even when the missing capability is something nobody thought to declare in advance — an unknown-unknown surfaces in a recorded inventory and cannot surface in a required-list check.

**Direct kinship, worth building together.** This is the same defect and the same fix as [[Every recorded step carries the directory and argv it actually ran with]] — a record honest about its outcome and silent about the one variable explaining it. Both are "write down the context you already have." If either is built, the other is nearly free, and a human choosing between them should probably not.

**Where it fails.** It is diagnosis, not prevention: the pass still burns its compute producing nothing, and someone still has to read the record. On a schedule nobody reads, it changes exactly nothing — which is a real risk here, given [[I need the tree's output to be actionable by compute alone, because my hours don't exist]].

**Cost.** Very small. The facts are available at startup; only the writing is missing.

⚠️ Unvalidated. Agent-ideated, 2026-08-02.
