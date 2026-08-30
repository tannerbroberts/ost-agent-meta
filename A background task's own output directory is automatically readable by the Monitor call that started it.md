---
type: Solution
source: 'TRANSCRIPT:0f28d01f-35fa-49f0-b085-89170e306ef8'
created: '2026-08-18'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[A background task can declare its own output path and have Monitor's read scope extended to exactly that path]]

When a run backgrounds a task that writes logs outside the session's normal allowed directories, extend Monitor's read scope to cover exactly the path that task itself declared it would write to, for the lifetime of that task — so a `tail` on the task's own log does not hit the same working-directory restriction meant for arbitrary file reads.

## Issues
- 2026-08-30 2026-08-30 unattended sweep, repo sight held: examined for a missing instrument and deliberately left without one. Recording the examination because this node carried no prior note and would otherwise be re-read from scratch by every firing that meets it in `solutionsMissingInstruments` — the same re-derivation cost its siblings already record on themselves. The artefact is Monitor, a harness tool: no spec under this repository's `test/` can assert anything about its read-scoping, so the mechanical half is structurally out of reach here. This is the identical blocker already recorded on the siblings "Monitor states its accepted command grammar up front rather than discovered by refusal" and "Adopt the platform's own job-control wait instead of maintaining a bespoke shell helper". The belief beneath this node, "A background task can declare its own output path and have Monitor's read scope extended to exactly that path", is feasibility about someone else's sandbox implementation, and its test is already on the standing queue as "Ask someone with the harness's sandbox implementation open whether a per-task scoped read grant is addable without widening the sandbox generally" — an ask, not a command. Fresh corroboration that the grant boundary is real and is discovered by refusal: this pass ingested TRANSCRIPT:28157325-0aa7-4b83-86f7-5292e9b7c509, in which a firing hit `Claude requested permissions to read from /Users/tanner/dev/OST-Agent, but you haven't granted it yet` twice on Glob before reaching the same source through ost_read_repo. That is evidence about the shape of the problem, not a reason to instrument the node. What a human should do: set the lane with `ost-agent lane --set`, since `ost_flag_humans_required` is withheld on the unattended surface. Not a skipped step.
