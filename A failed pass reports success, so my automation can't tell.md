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
