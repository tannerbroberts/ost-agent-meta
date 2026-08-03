---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Settle the known prompts as config and count how many new ones appear in a month]]

Most of these prompts have one right answer that never changes for this project — how to reconcile divergent branches, whether to overwrite on copy, which editor is not going to be opened. Decide each once, commit it as configuration, and no run ever meets the question. The operator answers in advance, deliberately, instead of being asked at the worst moment.

The evidence supports this strongly: a divergent-branch reconcile policy and a file-overwrite default are both one-line settings, and each of them ended a run.

**Compared to the alternatives.** The only option that lets the run continue rather than stopping cleanly, which is what the operator actually wants. The answers are also visible and reviewable in the repository rather than buried in a run's behaviour. It works only for prompts that have a stable right answer, and it must be maintained — a new tool in the chain brings a new prompt nobody has settled.

**What would make this the wrong pick.** Pre-answering questions is pre-committing to defaults, and a default committed once will eventually apply in a case where it is wrong. Silently reconciling divergent branches the same way every time is convenient until the once it should have stopped.
