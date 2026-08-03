---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

The human's work moves from carrying each result to setting up, once, a recurring export from the source into a folder the vault already watches. Most tools that hold experiment data can email, sync, or scheduled-export a sheet. The vault needs no new code at all: the drop folder it already reads is the destination.

**Compared to the alternatives.** Uniquely, this requires no engineering on the vault side — it is configuration, and it can be in place today rather than after an adapter is written. It also degrades gracefully, since a stale export is still an export. Against a pull adapter, it gives up structure: what arrives is whatever shape the source felt like emitting, and something still has to parse it. Against a webhook it gives up latency, running at the export's cadence rather than the experiment's.

**What would make this the wrong pick.** It quietly relocates the fragility rather than removing it. A scheduled export that silently stops — expired share link, changed sheet name, a source that stops sending — looks exactly like an experiment that produced no results, and the vault has no way to tell those apart. That failure mode is worse than a human forgetting, because a human eventually notices.
