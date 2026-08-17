---
type: Opportunity
source: 'TRANSCRIPT:00908faf-a23c-4c02-a792-9c402a4df8ac'
created: '2026-08-17'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed

Session transcripts from this vault's own unattended firings show a steady rate of tool_error and retry events — the run recovers and keeps going, so nothing surfaces the friction to the operator. Walking away with confidence means trusting not just that the run finishes, but that what it had to fight through along the way was nothing worse than noise. Right now there is no way to tell the difference between a run that sailed through and one that limped through eight retries, short of reading its transcript.

Is there more than one way to address this? Yes — a per-run friction summary surfaced at the end, a threshold-based alert only when a run is unusually rough, a rolling trend across firings, or simply nothing (accept that recoverable friction is not worth an operator's attention). That range is what makes this an opportunity rather than a solution in disguise.

**Sourced from:** repeated `TRANSCRIPT:*` friction records captured by the transcript-friction channel, each reporting one session's tool_error/retry counts, e.g. `TRANSCRIPT:00908faf-a23c-4c02-a792-9c402a4df8ac` (3 events: tool_error×1, retry×2). Corroborating session ids are appended below as they are mapped in — the pattern, not any single session, is the evidence.
