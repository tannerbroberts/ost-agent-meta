---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-24-friction-a-backgrounded-session-leaves-no-marker-of-where.md'
created: '2026-07-25'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[Every recorded step carries the directory and argv it actually ran with]]

When a run is stopped, backgrounded, or dies mid-work, nothing marks where it got to. The next run — or the operator — cannot tell finished work from abandoned work, so it either redoes, skips, or guesses.

Grounding: a builder pass was backgrounded mid-work on 2026-07-24 and the next pass had no way to tell what it had finished versus abandoned (agent-filed friction, kind: blocked).

Litmus: progress markers/checkpoints, a run journal, idempotent work detection, resumable pass state — multiple distinct ways to address. Distilled by the mapping agent from agent-self-reported observation; unvalidated. Distinct from [[What the agent learns doesn't accumulate over time]] (cross-session knowledge) — this is intra-run work-state.

## Issues
- 2026-07-27 OBSERVED TWICE IN ONE PASS, 2026-07-27 (eleventh pass) — and the gap is narrower and more fixable than this node's general framing.

`ost-agent loop step` records the phase, the command string, the exit code and the duration. It does NOT record the working directory the command ran in. Twice this pass I invoked `loop step ... -- npx vitest run` from the home directory instead of the repo; vitest collected all four sibling repos, exited 1, and the health record now carries a build step at exit 1 against a command that passes cleanly in its intended cwd. Both entries are left standing rather than edited — the exit codes are true, and laundering them is the one thing the seal discipline forbids.

The point is not the operator error. It is that the record is HONEST about the exit code and SILENT about the single variable that explains it, so the failure cannot be reproduced or diagnosed from the record alone. A reader six passes from now sees `bash -c npx vitest run -> exit 1` and has no way to distinguish a real regression from a mis-invocation.

Cheapest fix: `loop step` stores `cwd` (and arguably the resolved argv) alongside the exit code. It is one field, and it converts an unreproducible number into a reproducible one. Filed as friction this pass; see [[Resumable append-only process journal]] for the adjacent structure this would extend.
