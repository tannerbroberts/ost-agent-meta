---
type: Solution
status: shipped
created: '2026-07-27'
evidence: assertion
---
#Solution #evidence/assertion
[[The guard catches real laundering without refusing honest commands]]

**Shipped v0.21.0, commit `87164d6` on `main`.**

**The instance, observed rather than imagined.** A firing wrapped its build phase as `ost-agent loop step --phase build -- bash -c "npx vitest run 2>&1 | tail -25"`. `vitest` was not on the path. The shell printed `vitest: not found` -- and the step recorded **exit 0**, because a POSIX pipeline's status is its *last* command's, and `tail` succeeded at reading nothing. `runs.jsonl` gained a green build step for a command that never ran. Nothing surfaced it; it was found by reading the record back afterwards.

**Why this belongs under this opportunity and not next to it.** The parent is about a pass that dies and still exits 0. This is the same lie one layer down: the *step* that dies and still records 0. And the mechanism is worse, because the pass at least errored -- here the shell genuinely returned success, so no amount of care inside `loop step` would have caught it. `loop step` was not wrong to record what it was handed.

**What was actually wrong.** The tool accepted a command construction in which a red step **cannot come out red**. That is the definition of a check that is not a check, and this project's own doctrine is that you cannot assert health, only earn it. One laundered step is enough to make the entire file require corroboration, and a record that requires corroboration is not a record.

**The shape of the fix.** A shell `-c` script containing an unguarded pipeline is refused **before the child spawns and before anything is written**, so the laundered step never reaches the record at all -- the same contract the append-only tools use when handed bad input. The message names the command, the reason, and the repair.

**No override flag, deliberately.** `set -o pipefail` makes the pipeline report its first failing stage, which is the correct fix rather than a workaround. An `--allow-laundered-exit` would be reached for exactly when it does the most damage.

**What it does not touch:** direct `argv` commands (no shell between the tool and the process, nothing to launder), `||`, pipes inside single or double quotes, escaped pipes, and any script already enabling `pipefail`. Fifteen of the 33 new tests exist only to pin those, because a guard that refuses too much would push people back to unwrapped commands -- worse than the problem it solves.

**Verification observed:** 70 test files / 543 tests pass; `tsc` clean.

**This is the fifth variant this tree has met of 'a rule reports success while covering less than it claims', and the second to land in the instrument rather than the subject** (the first being the three defective plants found by the positive-control test in v0.20.0). The pattern is no longer a coincidence and should probably become an opportunity in its own right rather than a recurring note.

## History
- 2026-08-01 evidence: observed → assertion — demoted by the fifteenth pass — B3's rung-unearned guard (v0.23.0-line) shipped after this node was authored; its source is not a TRANSCRIPT: recording, so 'observed' was unearned. Demotion only, per rungs.ts's own remedy.
- 2026-08-05 unlinked "Does the guard catch real laundering without refusing honest commands" — moved under "The guard catches real laundering without refusing honest commands" — the belief this test measures now has a node of its own
- 2026-08-05 status: (none) → shipped — The node's own body records this as shipped: "Shipped v0.21.0, commit `87164d6` on `main`" — a shell `-c` script containing an unguarded pipeline is refused before the child spawns, with 33 new tests (15 of them pinning what must NOT be refused), 70 test files / 543 tests passing and tsc clean. Recorded as `shipped` by the 2026-08-05 unattended sweep because it sat in `solutionsMissingInstruments`, and a red-now instrument is impossible for behaviour that already ships: a spec asserting the guard would pass on arrival, so it could not fail and would give a builder no definition of done. Status corrected rather than an instrument invented — the same repair this sweep's predecessor applied to "Refuse a wiki-link that contains a newline". This says the mechanism is built; it does not say anyone has judged it worth having, which is still what its assumption test is for.

## Issues
- 2026-08-06 2026-08-06 In `solutionsMissingInstruments` while carrying `status: shipped` — do not write an instrument for this. A red-now command is impossible for shipped behaviour. There is also direct evidence the refusal is live: `ost_set_instrument`'s own tool description states it accepts a single spec-file command and "nothing else is accepted — no shell punctuation, no arbitrary command", which is at least part of this node's claim in present tense. The 2026-08-06 sweep declined to invent an instrument rather than write one whose only red is a missing file, and could not confirm the claim against the code because product-directory reads were denied and `ost_read_repo` was not granted on this surface. Flagged by a sibling node in the same era ("Refuse a wiki-link that contains a newline") as one of two that should be checked against the repository before anyone instruments them; this is that check being deferred a second time, which is worth a human's attention on its own. Systemic fix: "Work I already finished keeps coming back in the queue, so the pass can never say it is done".

## Checked against the repository — 2026-08-09 (presence only, not a recorded result)

**No test was run.** This node's Issues section records that the 2026-08-06 pass could not confirm the shipped claim because product-directory reads were denied to it. Repo sight was granted this pass, so the check was attempted — and the result is weaker than the one now recorded on the two sibling nodes, which is why it is labelled differently.

**What was actually established:** `test/loop/exit-laundering.test.ts` is present in `test/loop/`, listed through `ost_read_repo`. The filename matches this node's claim exactly, and it sits beside the loop's other guards (`stall`, `lock`, `health`, `degraded-pass-reporting`).

**What was not:** the file was not opened. A directory listing is evidence that a spec with that name exists; it is not evidence of what it asserts, that it passes, or that it covers the fifteen must-not-refuse cases this node says it does. Nobody should read this section as confirming the 33-tests/543-passing figure in the body above — that figure remains the author's own report.

The reason for stopping at presence: two sibling claims were verified properly this pass by reading `test/ost/vault-write-guard.test.ts` in full, and a third full read was not worth its cost against a claim that is already corroborated from another direction — `ost_set_instrument`'s own tool description states in present tense that it accepts a single spec-file command and "nothing else is accepted — no shell punctuation, no arbitrary command", which is part of this node's claim observable from the surface itself.

**For a human, or for a later pass with repo sight:** opening that file is a two-minute job and would upgrade this to the standard now set on "Refuse a wiki-link that contains a newline". The specific thing worth checking is the must-not-refuse set — direct `argv` commands, `||`, pipes inside quotes, escaped pipes, and scripts already enabling `pipefail` — because a guard that refuses too much is the failure this node names as worse than the problem it solves, and that half is the half no external observation corroborates.

## Verified against the repository — 2026-08-10 (not a recorded result)

**No test was run and nothing here clears a gate.** The 2026-08-09 pass stopped at a directory listing and asked a later pass with repo sight to open the file; this pass did, reading `test/loop/exit-laundering.test.ts` in full through `ost_read_repo`.

**The claim holds, including the half no external observation had corroborated.** Against `src/loop/exitLaundering.js` the spec asserts the observed case verbatim (`npx vitest run 2>&1 | tail -25` is detected, with shell and script named) plus pipelines to grep/tee, three-stage pipelines, bash's `|&`, pipelines after a semicolon, six shell spellings, and clustered `-lc` flags. The must-not-refuse set — the half this node called worse-if-wrong — is pinned explicitly: `set -o pipefail` (including clustered `set -eo`/`set -euo`), logical OR, pipes inside single and double quotes, escaped pipes, plain `&&` chains, direct argv with no shell, a non-shell binary taking `-c` (`python3 -c "print(1 | 2)"`), a shell invoked without `-c`, and degenerate argument lists that must not crash. A third block asserts the refusal message shows the refused command, names `set -o pipefail` as the fix, offers the no-shell alternative, and states nothing was written.

**What this does not settle.** That the spec passes — it was read, not executed — and nothing about desirability, which remains the assumption test's question. The standing conclusion is unchanged: this solution is shipped, a red-now instrument is impossible for it, and its recurrence in `solutionsMissingInstruments` belongs to "Work I already finished keeps coming back in the queue, so the pass can never say it is done".
