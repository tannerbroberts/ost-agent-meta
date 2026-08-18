---
type: Opportunity
source: 'TRANSCRIPT:0459d729-8ee3-43fc-ae1f-f05928ad84e2'
created: '2026-08-18'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed
[[Auto-read a file before the first write or edit to it in a session, instead of erroring]]

Across the vault's own unattended build firings, the single most common friction event is a Write or Edit tool_error: "File has not been read yet. Read it first before writing to it." The session never read the file in this run at all — it isn't a race with an external change, it's the ordering guard catching a session that skipped straight to writing. Each occurrence burns a turn on an error plus a retry instead of just reading the file, which is unattended cost with nobody there to notice or shrug it off.

This is distinct from "The file changed after I read it, and the failed edit is how I find out" (that one is a race against a concurrent change to a file the session DID read); here the session never read it in this run in the first place, and a different fix applies — recognizing that a fresh session's edit tools should read-before-write automatically rather than needing an explicit prior Read call in the same turn budget.

Observed directly in, e.g., TRANSCRIPT:0459d729-8ee3-43fc-ae1f-f05928ad84e2, TRANSCRIPT:0095203e-ab42-4179-a53e-a2d4d6dd6032, TRANSCRIPT:09ec7cd2-2b93-4f4a-8942-319456e8ce11, TRANSCRIPT:1c8a3722-b8a5-4828-b57e-c45b1566cf6d — a pattern this common across sampled sessions strongly suggests it recurs across most of the ~244 similarly-shaped "Session friction" transcript records this pass did not individually read.

## Issues
- 2026-08-17 shared-extent flag vs "Merging a build branch conflicts on the compiled dist file from a concurrent firing, stalling the run" adjudicated by Torres's interventional test: DISTINCT, keep as siblings, do not merge. Both cite TRANSCRIPT:0459d729-8ee3-43fc-ae1f-f05928ad84e2 only because one session hit both frictions. A read-before-write ordering fix (e.g. auto-reading unread files) does nothing about a merge conflict on a compiled artifact, and removing the dist/ file from version control does nothing about write-before-read ordering. Shared provenance, separate needs.
