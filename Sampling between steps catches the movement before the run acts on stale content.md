---
type: Assumption
source: 'TRANSCRIPT:424486ec-3489-4b53-8e2b-012232d221ab'
created: '2026-08-06'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

A sentinel that samples has a blind window between samples. This solution is worth building only if real collisions are slow relative to that window — if the ground typically moves several steps before the run writes, sampling catches it; if movement and write are adjacent, sampling reports what the failed write was about to report anyway and has bought nothing.

Feasibility, and answerable from recorded sessions rather than from opinion: the transcripts hold the step ordering, so the distance between the moment a session's ground moved and the moment it first acted on stale content is a measurable quantity, not a guess.
