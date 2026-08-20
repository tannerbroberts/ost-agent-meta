---
type: Solution
source: 'agent-ideation:2026-08-20-unattended-sweep'
created: '2026-08-20'
evidence: assertion
---
#Solution #build-loop #unvalidated #evidence/assertion

**Mechanism.** `examples/automation/build-pass.sh` stops telling the model to Write `$REPORT` and instead captures the model's final message itself — `claude -p` output into the report path, with the prompt told that its last paragraph *is* the report. The script already owns every other write to that file (`report()`, `prefix_lineage()`); the model's Write is the only one routed through the harness's read-before-write guard, and it is refused on the first attempt every firing because the script has just pre-written the file and the session has never read it.

**Why this and not the siblings.** The three solutions beside it — auto-read before first write, warn instead of reject, skip the guard for self-created files — all change the harness, which this product does not own; the Issues entries on this branch record that as the reason no instrument could ever be written for them. This one changes a file in this repository and, by the count recorded on the parent (94 of 160 instances are the report file), removes the majority of the friction without touching the guard. It does nothing for the other 66 — Edits to source and test files mid-build — which remain the harness-side need.

**Where it fails.** The model's final message may carry more than the report (a closing sentence about what it did, a tool result quoted back), so the script needs either a delimiter convention or a rule that the last paragraph is the report, and `prefix_lineage()` would then run on every firing rather than only when the model wrote. A narrower variant within the same mechanism — have the prompt `Read` the report before it Writes — keeps the model's Write and spends one cheap tool call instead of one refused one; it is the fallback if capturing stdout proves awkward.

**Cost.** A change to one shell script and its prompt text, plus a spec asserting the prompt no longer requests the write.

⚠️ Unvalidated. Agent-ideated from the count on the parent node; no operator has said the wasted turn matters to them.
