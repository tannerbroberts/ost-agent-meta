---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-25-friction-a-pass-that-dies-on-a-driver-error-still-exits-0.md'
created: '2026-07-25'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed
[[Nonzero exit code and failure summary when a pass errors]]
[[Status and digest lead with the last failed run]]
[[Supervisor heartbeat consumes run journals and alerts on error]]

**The need (operator's voice):** "P2_map died on an auth error and still exited 0, wrote a commit, and printed a tidy summary. If that had been my nightly cron, it would no-op forever while looking perfectly healthy."

**Why it matters:** unattended operation stands or falls on failure being *visible to machines*. The run journal records the error faithfully — but nothing that schedules, monitors, or alerts reads prose. Observed mechanically 2026-07-25T02:00:38Z (exit 0, commit 8038dfe9, error in `.ost-agent/runs/…P2_map.json`).

**Litmus (more than one way?):** yes — exit codes, status surfacing, supervisor-consumed journals, push alerts are all distinct answers.

## Shipped — 2026-07-25, v0.5.0 (feasibility evidence, not demand)

Both leading solutions under this node were built and released in `ost-agent` v0.5.0 (commit `f091b04`). This node was created from an observed friction on 2026-07-25T02:00:38Z and closed as a build within the same day — the fastest observed-to-shipped path in this vault's history.

- [[Nonzero exit code and failure summary when a pass errors]] — `ost-agent run` exits **1** and prints `<process> FAILED: <error>` to stderr. `ost-agent schedule` logs the same line and stays up.
- [[Status and digest lead with the last failed run]] — `ost-agent status` leads with process, timestamp, the error verbatim, and the journal path, above the node counts, and labels each process's last run `ok`/`FAILED`.

**The open trade-off named on the exit-code node was decided, and here is the reasoning so it can be overruled.** Partial passes (work committed, then an error) exit **1**, not a distinct code. One code meaning "do not trust this run" is the contract cron, launchd, and CI already speak; a third code would need every consumer to learn a new vocabulary to express something the journal already records precisely. Whatever landed before the error is still in the commit and still in the journal. If a supervisor later needs to distinguish them, the journal is where that distinction should be read from, not the exit status.

**What this does NOT do.** Nothing here notices a pass that never *starts* — a cron that stops firing, a machine that sleeps, a container that never came back. Exit codes only speak when a process runs. That silence is [[Supervisor heartbeat consumes run journals and alerts on error]]'s job and it is unbuilt.

**Rung unchanged: `observed`.** A shipped fix is not evidence that anyone but this operator needs it.

## Issues
- 2026-07-25 STANDING FAILURE, STILL RED (observed 2026-07-25, pass 4). `ost-agent status` on
this vault still leads with a failed run: P2_map at 2026-07-25T02:00:38Z, 'Could not
resolve authentication method. Expected either apiKey or authToken to be set.' The
scheduled cron passes have therefore not been running — no ANTHROPIC_API_KEY exists
in the loop's environment. Every tree change since has come from the bootstrap loop
driving the append-only tools directly, which needs no key.

Recorded as evidence FOR this opportunity's premise working as designed: v0.5.0's
exit-code and status-surfacing change is why this is visible at all, four passes
later, instead of silently absent. Not fixed here — supplying a credential is a
human's call, and the same one as
[[Bundled local model for zero-credential trial]].
- 2026-07-26 undefined
- 2026-07-26 **Hygiene — a destroyed annotation, flagged not repaired (2026-07-26).** One or more lines in this node read `- <date> undefined`. That is not a note anybody wrote: `ost_annotate` was called with `note` instead of its declared `issue` field, nothing validated the call, and the literal string "undefined" was appended in place of the content. The original text was never written anywhere and is unrecoverable. Fourteen such lines exist across the two live vaults, written by several passes over three days. The cause is closed in ost-agent v0.17.0, which refuses a tool call that does not match the schema the tool itself declares. **Left in place deliberately:** this vault is append-only, and rewriting history to hide a bad write is exactly the action this product refuses — including when the product is the one that made it. Full account: [[A tool call I got slightly wrong destroyed the note I was filing]].


## A third shape of the same failure, and this one is not about exit codes — 2026-07-26

This node has always been about a run that **errors and reports success**. The sibling
product just supplied a variant that no exit code could have caught, and it is worth
recording here rather than as its own opportunity, because the operator's complaint is
identical: *the signal was there, and it carried no information.*

**What happened.** `tetrix-game-monorepo`'s frontend suite had reported **8 failures across
5 files** on `master` for at least seven passes. Every pass that touched the repo dealt with
it the same way — run the suite before the change, run it after, confirm the failures are
*identical*, and proceed. That ritual is in three separate pass notes in the sibling vault.
It is a human performing, by hand and by eye, the comparison a gate exists to perform.

**The cost was not hypothetical, and this pass measured it.** The eight were two entirely
unrelated defects that had been sitting behind one undifferentiated "still 8, same as
before" for weeks:

- **Three were path rot.** Three suites hard-coded deep stylesheet paths; a refactor moved
  the play area to another folder. Every invariant they guard was *still true* of the files
  at their new addresses. The guards had simply been reading a missing file.
- **Five asserted a design a human deliberately replaced.** A saturated reskin swapped two
  surfaces from one token system to another and left the tests behind.

Neither was a product regression. Both were the test losing track of the code — and
crucially, **a real regression arriving during those weeks would have been invisible**,
because it would have presented as "8 failures, same as before" only if it happened to land
in the same files, and as "9 failures" otherwise, in a suite nobody could read at a glance.
All 8 are fixed (`tetrix-game-monorepo` `3aa4ef2`); the suite is green, 461 passing.

**Why this belongs under this opportunity and not a new one.** The three solutions here are
all about making a *failure* legible to a machine. This is the mirror image: a failure so
legible and so constant that it became the baseline, and the comparison moved into a human's
head. An exit code cannot help — the suite exits non-zero, correctly, every time. What was
missing is any notion of an *expected* failure set, so that "the same 8" and "a different 8"
are different events.

**Deliberately not proposed as a solution here.** Baselining a red suite is a well-known
idea with a well-known failure mode: the baseline becomes permanent and the quarantine
becomes the product. The alternative this pass took — fix them — worked, and took one pass.
Which is right in general is a judgement, and the party that just spent a pass on it is not
a neutral one.

**Rung unchanged: `observed`.** Two mechanically observed instances, both inside this
building, on systems this loop operates. Still nothing from an outside operator.
