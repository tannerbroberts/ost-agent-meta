---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-25-friction-a-pass-that-dies-on-a-driver-error-still-exits-0.md'
created: '2026-07-25'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Five-second status glance test after a failed run]]

**The idea.** `ost-agent status` (and any digest) surfaces the most recent failed run journal first — error, when, which pass — before node counts. Failure becomes the first thing a human sees, not a JSON file to spelunk.

**Contrast with siblings:** human-visibility lane; complements rather than replaces the exit-code floor. Reuses the run journals that already exist and are already honest.

**Trade-off:** only helps if a human looks; unattended operation still needs the sibling.

## Built — 2026-07-25, v0.5.0

`ost-agent` commit `f091b04`. `ost-agent status` now opens with `⚠ Last run FAILED — <process> at <time>`, the error verbatim, and the journal path, before any node count; every process's last run is labelled `ok`/`FAILED` in the run list. The prediction on this node held — it reused the run journals that already existed and were already honest, and needed no schema change.

**One design decision worth recording.** A corrupt or unparseable journal is skipped rather than thrown on. The alternative (fail loudly on a bad file) would let one unreadable journal hide a genuine failure recorded in a different one, which is the exact failure mode this whole branch exists to prevent.

**The trade-off this node named is unchanged and unaddressed:** this only helps if a human looks. Unattended operation still rests entirely on the exit-code sibling, and on a supervisor that nobody has built.

**The digest half of this node is not built** — there is no digest. Only `status` was touched.
