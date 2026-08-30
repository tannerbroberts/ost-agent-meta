---
type: Assumption
source: 'agent-ideation:2026-08-30-unattended-sweep'
created: '2026-08-30'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion
[[A validate-only call names every objection the writing call would, and leaves the vault byte-identical]]

**The belief, stated so it could be false:** the checks a mutating tool runs can be executed in full without any of them producing a side effect, so a `validate: true` call returns the same objections a real call would and leaves no node file, no commit, and no ledger line.

**Why it could be false.** Some checks are not pure. A check that resolves a parent, reads the tree, or consults the ledger may itself write — the usage trace is stamped at dispatch, and `enqueueCommit` runs on the mutating path. If validation cannot be separated from the write cleanly, a validate-only mode either misses the checks that matter most (the tree-dependent, disqualifying ones) or quietly leaves traces, and both defeat the point: a mode that reports fewer objections than the real call is worse than no mode, because a caller would trust a clean validate and still be refused.

**Risk category:** feasibility.

**What this assumption is NOT.** It is not the claim that a caller will use the flag. That belief — whether an agent holding a validate-only mode spends a call on it before a write it is unsure about — is this candidate's sharpest risk and is deliberately not what this node states, because it is behavioural and no spec reaches it. It is recorded here in plain text so a human can decide whether to give it a node of its own: nothing measures it today, and a flag nobody uses fixes nothing.
