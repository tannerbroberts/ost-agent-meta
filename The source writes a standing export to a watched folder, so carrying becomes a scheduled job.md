---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A scheduled export keeps arriving, and a stopped one does not look like an empty experiment]]

The human's work moves from carrying each result to setting up, once, a recurring export from the source into a folder the vault already watches. Most tools that hold experiment data can email, sync, or scheduled-export a sheet. The vault needs no new code at all: the drop folder it already reads is the destination.

**Compared to the alternatives.** Uniquely, this requires no engineering on the vault side — it is configuration, and it can be in place today rather than after an adapter is written. It also degrades gracefully, since a stale export is still an export. Against a pull adapter, it gives up structure: what arrives is whatever shape the source felt like emitting, and something still has to parse it. Against a webhook it gives up latency, running at the export's cadence rather than the experiment's.

**What would make this the wrong pick.** It quietly relocates the fragility rather than removing it. A scheduled export that silently stops — expired share link, changed sheet name, a source that stops sending — looks exactly like an experiment that produced no results, and the vault has no way to tell those apart. That failure mode is worse than a human forgetting, because a human eventually notices.

## History
- 2026-08-05 unlinked [[Set up one scheduled export and check every week whether it is still arriving]] — moved under [[A scheduled export keeps arriving, and a stopped one does not look like an empty experiment]] — the belief this test measures now has a node of its own
