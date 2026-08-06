---
type: Solution
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A pass can enumerate its own senses and their state without being told what it tried to use]]

**The idea.** Every pass closes with a census of its senses — configured, wired, reached for, refused — the way `ost_ingest_inbox` already reports one line per channel including the disabled ones. Nothing is blocked; the degradation simply stops being silent.

**Why this shape, given the precedent already in the product.** The ingest report is the model and it works: "[atlassian] disabled — turned off in ost.config.yaml (adapters.atlassian.enabled: false)" tells the reader that a channel was considered and deliberately skipped, so an empty result is legible rather than ambiguous. No equivalent exists for the senses a pass reads *with*, which is why a pass that never saw the product repo reports exactly like one that read it thoroughly.

**What it buys that blocking does not.** The operator is asleep. A pass that refuses to start produces a night of nothing; a pass that runs degraded and says so produces work plus a repair instruction, and the operator reads both in the morning. It also composes with the other two rather than competing — a sense census is worth having even after config validation, because it covers the harness-grant half that config cannot see.

**Where it fails.** A report at the end is a report nobody may read, and this loop's whole problem is that its output already exceeds what anyone reviews. It changes nothing about the pass that produced the degraded work — the invented-path instruments still got written, still sit in the tree, and still look identical to grounded ones to any later reader who is not holding the census. Making a failure visible is not making it not happen, and the honest claim for this candidate is only the former.

**Compared with its siblings.** Strictly weaker than "Every path the config declares is checked when the config is read" at preventing the loss, and strictly better at not costing a night. "The step that needs the product repo declares it required" is the middle path. This is the one to ship first if the others are contested, because it is nearly free and it produces the measurements the other two would be judged by.

⚠️ Unvalidated. Agent-ideated.
