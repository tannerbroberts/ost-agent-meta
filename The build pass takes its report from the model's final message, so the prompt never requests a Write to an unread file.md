---
type: Solution
source: 'agent-ideation:2026-08-20-unattended-sweep'
created: '2026-08-20'
evidence: assertion
authorship: machine
---
#Solution #build-loop #unvalidated #evidence/assertion
[[The model's report can be captured from its final output by the script, without the model writing a file]]

**Mechanism.** `examples/automation/build-pass.sh` stops telling the model to Write `$REPORT` and instead captures the model's final message itself — `claude -p` output into the report path, with the prompt told that its last paragraph *is* the report. The script already owns every other write to that file (`report()`, `prefix_lineage()`); the model's Write is the only one routed through the harness's read-before-write guard, and it is refused on the first attempt every firing because the script has just pre-written the file and the session has never read it.

**Why this and not the siblings.** The three solutions beside it — auto-read before first write, warn instead of reject, skip the guard for self-created files — all change the harness, which this product does not own; the Issues entries on this branch record that as the reason no instrument could ever be written for them. This one changes a file in this repository and, by the count recorded on the parent (94 of 160 instances are the report file), removes the majority of the friction without touching the guard. It does nothing for the other 66 — Edits to source and test files mid-build — which remain the harness-side need.

**Where it fails.** The model's final message may carry more than the report (a closing sentence about what it did, a tool result quoted back), so the script needs either a delimiter convention or a rule that the last paragraph is the report, and `prefix_lineage()` would then run on every firing rather than only when the model wrote. A narrower variant within the same mechanism — have the prompt `Read` the report before it Writes — keeps the model's Write and spends one cheap tool call instead of one refused one; it is the fallback if capturing stdout proves awkward.

**Cost.** A change to one shell script and its prompt text, plus a spec asserting the prompt no longer requests the write.

⚠️ Unvalidated. Agent-ideated from the count on the parent node; no operator has said the wasted turn matters to them.

## Definition of done

"The build prompt no longer instructs a Write to the report file, and the script places the captured report itself"

```
npx vitest run test/automation/build-pass-report-channel.test.ts
```

Red today as `no-spec` — the file is not written. The test node names the two assertions it must hold (prompt heredoc contains no Write-the-report instruction; executable lines route `claude -p` output into `$REPORT`), both of which fail against today's `examples/automation/build-pass.sh`. A green proves the prompt stopped requesting the refused operation; it says nothing about whether anyone wanted the turn back.

## Issues
- 2026-08-23 2026-08-23 unattended sweep, repo sight held — a finding that could upgrade this node's red from `no-spec` to a failing assertion, but which needs a decision this surface cannot make. The Definition of done names a NEW file, `test/automation/build-pass-report-channel.test.ts`, so its red is the weakest kind: absent-file, identical for any question written on it. Read first-party this pass: `test/release/build-pass-surface.test.ts` already exists and already asserts over `examples/automation/build-pass.sh`, and it already does the exact thing this node's two assertions need — it splits the file into `executable` (comments stripped) and `commands` (prompt heredoc cut out) precisely so that "what the script runs" can be asserted separately from "what the prompt says", and its `shipping is local` block greps the prompt heredoc for instructions to the builder (`do not run 'gh pr checks'`, `Do not merge`). Both of this node's assertions — prompt heredoc contains no Write-the-report instruction; executable lines route `claude -p` output into `$REPORT` — fit that file's existing harness with no new scaffolding. Why this pass did not act on it: naming `test/release/build-pass-surface.test.ts` as the instrument would be GREEN on arrival (every assertion in it passes today), which `ost_set_instrument` rightly refuses, and an unattended discovery pass cannot add the failing assertion that would make it red. So the choice between "new file, weak red" and "existing file, strong red once a builder adds two assertions" is a builder's or an attended pass's, not this one's. Recorded because the second option was not visible to the pass that wrote the Definition of done, and it is the difference between handing a builder "create this file" and handing them one assertion to make true.
