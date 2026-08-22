---
type: Solution
source: 'agent-ideation:2026-08-21-unattended-sweep'
created: '2026-08-22'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**Variation dimension: where it lives — upstream at the adapter, before anything reaches the vault. All three siblings act downstream, on a queue that already exists.** The transcript adapter stops writing one record per session. It writes one record per *friction shape* — `File has not been read yet`, `permissions to read from`, `Blocked: sleep N followed by`, and so on — and each new session updates its shapes' records in place: occurrence count, session count, first and last seen, a sample. A shape nobody has seen before creates a record, which is exactly the event a sweep should be interrupted for.

The queue then holds roughly as many transcript records as there are distinct failure modes — a number that grows when the product breaks in a new way and stays flat when it breaks in an old one. That is the shape a work queue is supposed to have.

**Compared to its siblings.** "Cluster friction records by signature before the queue sees them" is the nearest, and the difference is not cosmetic: clustering groups records that already exist, so 385 files are still written, still stored, and still counted somewhere. This one never creates them. "Let a friction record corroborate an existing opportunity" and "Record a read-and-skipped judgement" both leave the per-session record and add a way to dispose of it — they make the queue drainable, this makes it small.

**What it deliberately gives up, and it is the real cost.** Per-session records are the raw material every census on this tree is built from. The counts on "The unattended run is scoped for tools nobody granted it" are *per session* — "83 across 28 sessions", "eight consecutive denials in one firing" — and the 2026-08-21 recount could isolate a single regressing session precisely because each session had its own file. Rolling counters keep totals and lose the per-session distribution, which is where every finding on that node actually came from. Any honest version of this keeps the raw per-session data somewhere the vault does not treat as work; that is a real design constraint, not a footnote, and it may be what sinks the candidate.

**What would make this the wrong pick.** If shapes turn out to be hard to identify without judgement — the same question the ingest-time tripwire candidate on the staleness node runs into — the adapter is a bad place to be making that call, because a mis-shaped record is now the only record of the event rather than a wrong grouping over records that still exist. And a shape-keyed record is a node whose content changes under a `source:` that stays fixed, which is a provenance property nothing in this vault currently has and every downstream reader assumes away.

**Distilled from a measurement, not from ideation.** The channel split recorded on the parent this pass — 73 of 73 non-transcript records mapped, 361 of 385 transcript records not — is what says the asymmetry belongs to one adapter rather than to the queue, and no sibling addresses it there.

⚠️ Unvalidated. Agent-ideated, 2026-08-21 unattended sweep.
