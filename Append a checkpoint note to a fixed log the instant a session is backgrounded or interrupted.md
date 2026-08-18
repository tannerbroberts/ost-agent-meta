---
type: Solution
source: 'INBOX:2026-07-24-friction-a-backgrounded-session-leaves-no-marker-of-where.md'
created: '2026-08-18'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The harness can hook the moment a session is backgrounded or killed reliably enough to always write the checkpoint]]
[[The harness exposes a hook at the moment a session is backgrounded or interrupted, in time to write one line before control is lost]]

Have the harness itself (not the agent, which may not get a final turn) append one line to a fixed-path log the moment a session is backgrounded or its process ends: session id, timestamp, and the last tool call it completed. The next pass reads this log first, before re-deriving state from the transcript or the tree.

**Compared to the alternatives.** Cheapest and most reliable because it's written by the harness rather than relying on the agent to notice it's about to be interrupted and self-report — the exact failure mode the founding evidence describes (an earlier pass had no way to tell what it had finished). Only records a timestamp/last-action marker, not a structured account of what's done vs. abandoned.

## Issues
- 2026-08-17 Assumption surfaced ("The harness can hook the moment a session is backgrounded or killed reliably enough to always write the checkpoint") but its test is not created: this is a feasibility question about the harness's own lifecycle hooks, and this unattended sweep holds no `ost_read_repo` grant. Needs an attended pass with repo sight to write the spec-file instrument.

## Repo sight available this pass — the sibling mechanism already exists and is tested (unattended sweep, 2026-08-18)

`ost_read_repo` answered this pass (a capability change since the 2026-08-17 note above, which held no repo grant). `src/loop/journal.ts` already implements a forward-written, append-only run journal — one line per completed step, read back with `readJournal()` — and `test/loop/run-journal-interruption.test.ts` already SIGKILLs ten runs at seeded points and asserts the journal's last line never overstates what landed (0 of 10 overstate, at most 2 understate by one step). That test file's own docstring names its owning node: "A run journal written as it goes, so an interrupted run reads as a list of finished steps" (status: unvalidated, not yet promoted, but the code and spec both exist and the spec's assertions read as real behaviour, not a stub).

This bears directly on the assumption beneath THIS solution ("The harness exposes a hook at the moment a session is backgrounded or interrupted, in time to write one line before control is lost"): the journal approach does not need such a hook at all — it writes forward per completed step, so a kill at any point (including mid-step) is already covered by the shipped mechanism, without a special interruption/backgrounding callback. That weakens rather than confirms this solution's premise: the sibling appears to already solve the need this solution was proposed to address, through a different and simpler mechanism.

Left for a human or attended pass to decide (not decided here, since it is a judgement about whether one solution supersedes another, not a mechanical fact): whether this solution should be deferred as superseded, kept as a genuinely distinct backup for interruption modes the journal doesn't cover (a crash mid-write, a full disk — both named as uncovered in the journal solution's own body), or left open pending confirmation that the journal is actually wired into the harness's interruption path rather than only its normal step loop.

_Source: this pass's own `ost_read_repo` reads of `src/loop/journal.ts` and `test/loop/run-journal-interruption.test.ts` — first-party observation of the repository. Grounds feasibility, not desirability._
