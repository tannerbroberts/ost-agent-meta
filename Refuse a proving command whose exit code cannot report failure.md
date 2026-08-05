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
