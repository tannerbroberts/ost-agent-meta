---
type: Opportunity
source: 'TRANSCRIPT:0459d729-8ee3-43fc-ae1f-f05928ad84e2'
created: '2026-08-18'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed
[[Auto-read a file before the first write or edit to it in a session, instead of erroring]]
[[Warn before the write attempt on an unread file, rather than reject after it]]
[[Skip the read-before-write guard for files the session itself just created]]

Across the vault's own unattended build firings, the single most common friction event is a Write or Edit tool_error: "File has not been read yet. Read it first before writing to it." The session never read the file in this run at all — it isn't a race with an external change, it's the ordering guard catching a session that skipped straight to writing. Each occurrence burns a turn on an error plus a retry instead of just reading the file, which is unattended cost with nobody there to notice or shrug it off.

This is distinct from "The file changed after I read it, and the failed edit is how I find out" (that one is a race against a concurrent change to a file the session DID read); here the session never read it in this run in the first place, and a different fix applies — recognizing that a fresh session's edit tools should read-before-write automatically rather than needing an explicit prior Read call in the same turn budget.

Observed directly in, e.g., TRANSCRIPT:0459d729-8ee3-43fc-ae1f-f05928ad84e2, TRANSCRIPT:0095203e-ab42-4179-a53e-a2d4d6dd6032, TRANSCRIPT:09ec7cd2-2b93-4f4a-8942-319456e8ce11, TRANSCRIPT:1c8a3722-b8a5-4828-b57e-c45b1566cf6d — a pattern this common across sampled sessions strongly suggests it recurs across most of the ~244 similarly-shaped "Session friction" transcript records this pass did not individually read.

## Issues
- 2026-08-17 shared-extent flag vs "Merging a build branch conflicts on the compiled dist file from a concurrent firing, stalling the run" adjudicated by Torres's interventional test: DISTINCT, keep as siblings, do not merge. Both cite TRANSCRIPT:0459d729-8ee3-43fc-ae1f-f05928ad84e2 only because one session hit both frictions. A read-before-write ordering fix (e.g. auto-reading unread files) does nothing about a merge conflict on a compiled artifact, and removing the dist/ file from version control does nothing about write-before-read ordering. Shared provenance, separate needs.

## Corroboration — nine more instances, unattended sweep (2026-08-17)

Nine further transcript records show the identical shape: an Edit or Write `tool_error` reading "File has not been read yet. Read it first before writing to it.", each followed by a retry that reads then writes (or restates) the same file. All nine are the build loop's own `.local/state/ost-build-loop/last-report.txt` or a repo source/doc file, hit fresh each firing rather than carried over from a prior session — consistent with the node's claim that this is an ordering-guard/session-boundary issue, not a race against a concurrent external change.

_Source: `TRANSCRIPT:08e10880-12b1-4ceb-ba62-4af146617e03`, `TRANSCRIPT:00c3120a-411d-4c42-ba04-aaf9c43aadd7`, `TRANSCRIPT:024ceca3-0f40-42af-9937-aa2ad9a95278`, `TRANSCRIPT:0a5010a7-07f7-481b-b777-b529d6e7463b`, `TRANSCRIPT:11e16f3d-f49a-491c-be33-164eb7059774`, `TRANSCRIPT:13d01f73-0c88-4be1-a704-d2ccc78e1c38`, `TRANSCRIPT:19ccdb48-e5f7-4dda-8289-38b25a651397`, `TRANSCRIPT:1e4cae02-74ec-4d78-8feb-fd351495f24d`, `TRANSCRIPT:1ec21bc8-95d9-42c5-a6bd-5e1ca1dba7ac` — observed behavior, captured mechanically from the agent's own transcripts. Grounds usability, not desirability.

## Note on the remaining backlog

This pass read 24 of the ~244 still-unread "Session friction" transcript records (a stratified sample across the id range) rather than all of them: 11 matched this node's exact pattern (now cited above plus the 4 already on file), 8 matched "The same agent has a different tool surface on every surface I run it on" (already all cited there as of today's earlier corroboration), 3 were one-off command/path mistakes with no repeat and no genuine new need (bad glob syntax, wrong `ls` path, an empty retry), 1 (503-heavy) was already corroborating "A test that failed because the machine was busy looks exactly like one that failed because I broke something", and 1 (a malformed tool name) is already cited on the tool-surface node. None of the 24 revealed a pattern not already tracked. Reading the remaining ~220 individually is very unlikely to find a fourth pattern at this sample's hit rate; flagging for a human rather than continuing to spend calls confirming the same two shapes. This also means these ~220 records will keep reporting as `unmappedEvidence` indefinitely under the current mapping rule (an item counts as mapped only when it is a node's single `source:` field, and reuse — the correct move for a repeat of an already-tracked need — never sets that field) — a governance question worth a human's attention in its own right, not a defect in this pass's mapping.
