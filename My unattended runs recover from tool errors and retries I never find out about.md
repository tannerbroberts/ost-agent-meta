---
type: Opportunity
source: 'TRANSCRIPT:00908faf-a23c-4c02-a792-9c402a4df8ac'
created: '2026-08-17'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed
[[Append a one-line friction summary to the run's own completion report]]
[[Alert only when a run's friction count crosses a set threshold]]
[[Surface a rolling friction trend across the last N firings, not per-run]]

Session transcripts from this vault's own unattended firings show a steady rate of tool_error and retry events — the run recovers and keeps going, so nothing surfaces the friction to the operator. Walking away with confidence means trusting not just that the run finishes, but that what it had to fight through along the way was nothing worse than noise. Right now there is no way to tell the difference between a run that sailed through and one that limped through eight retries, short of reading its transcript.

Is there more than one way to address this? Yes — a per-run friction summary surfaced at the end, a threshold-based alert only when a run is unusually rough, a rolling trend across firings, or simply nothing (accept that recoverable friction is not worth an operator's attention). That range is what makes this an opportunity rather than a solution in disguise.

**Sourced from:** repeated `TRANSCRIPT:*` friction records captured by the transcript-friction channel, each reporting one session's tool_error/retry counts, e.g. `TRANSCRIPT:00908faf-a23c-4c02-a792-9c402a4df8ac` (3 events: tool_error×1, retry×2). Corroborating session ids are appended below as they are mapped in — the pattern, not any single session, is the evidence.

## Corroborating sessions

Same pattern (tool_error/retry counts from unattended firings), each read and confirmed to match before citing:
- TRANSCRIPT:0095203e-ab42-4179-a53e-a2d4d6dd6032
- TRANSCRIPT:00c3120a-411d-4c42-ba04-aaf9c43aadd7
- TRANSCRIPT:022e473f-670e-4455-ac06-6a7cfc60ba60
- TRANSCRIPT:024ceca3-0f40-42af-9937-aa2ad9a95278
- TRANSCRIPT:030e5db3-9414-441f-9221-b4a984c11825
- TRANSCRIPT:03b2fe6f-0338-4243-bcb4-5d908a89514f
- TRANSCRIPT:054b78fc-df16-44ff-b394-760b30f34cb3
- TRANSCRIPT:08f7d98f-24bd-46c0-a5ad-c17d53c4bbca
- TRANSCRIPT:09ec7cd2-2b93-4f4a-8942-319456e8ce11
- TRANSCRIPT:0a5010a7-07f7-481b-b777-b529d6e7463b
- TRANSCRIPT:0e0cd6f3-7541-4221-a6f1-efe977d0e2e2
- TRANSCRIPT:0ffc6652-f150-46d0-8a53-732ad64d4b66
- TRANSCRIPT:11e16f3d-f49a-491c-be33-164eb7059774
- TRANSCRIPT:13d01f73-0c88-4be1-a704-d2ccc78e1c38
- TRANSCRIPT:14c9afa5-ff0d-46b9-ba9b-c068c08eec63
- TRANSCRIPT:1515b876-9426-4fd8-8259-471f2aba7da1
- TRANSCRIPT:19ccdb48-e5f7-4dda-8289-38b25a651397
- TRANSCRIPT:1a8f25fb-1259-4b80-8b53-32fbfde38e54
- TRANSCRIPT:1b5a7f48-abaf-4958-8317-d2df1ed37e08
- TRANSCRIPT:1c8a3722-b8a5-4828-b57e-c45b1566cf6d
- TRANSCRIPT:1d62c716-4c49-40ec-84fe-2c849012d3f2
- TRANSCRIPT:1e4cae02-74ec-4d78-8feb-fd351495f24d

## Corroborating sessions — 2026-08-17 unattended sweep
Read and confirmed to match the same pattern before citing:
- TRANSCRIPT:1ec21bc8-95d9-42c5-a6bd-5e1ca1dba7ac (3 events: tool_error×2, retry×1 — Edit/Write "file not read yet", Bash retry)
- TRANSCRIPT:d231305b-c425-4597-9fd7-b7a8872f9c1d (3 events: tool_error×2, retry×1 — a Read tool_error worth noting on its own: "File content (409.8KB) exceeds maximum allowed size (256KB)", plus a Write "file not read yet")
- TRANSCRIPT:fee7afb0-c0d1-4ee7-ad54-3ee323cbb114 (2 events: retry×2 — on mcp__ost-agent__ost_ingest_inbox and mcp__ost-agent__ost_next_work themselves)

## Issues
- 2026-08-17 unattended sweep — 250 more TRANSCRIPT friction records remain in `unmappedEvidence` beyond the three cited above (253 total this pass, 2 non-transcript). Citing each individually is diminishing-return busywork at this scale: the node's own prose already says "the pattern, not any single session, is the evidence," and this bucket already has 25 corroborating citations. Recommend a human deprioritize further one-by-one manual citation here in favor of shipping "Cluster friction records by signature before the queue sees them" (already proposed beneath this node's sibling), which is the mechanism designed to absorb exactly this volume. Also worth a human's attention: TRANSCRIPT:d231305b's Read tool_error (409.8KB file exceeding a 256KB read cap) is a distinct, possibly novel failure shape within this pattern — a large-file read limit hit during an unattended firing — rather than the usual "file not read yet" retry loop.

## Corroborating sessions — 2026-08-18 unattended sweep
Read and confirmed to match the same pattern before citing:
- TRANSCRIPT:205477ec-b356-413f-b5f2-3a9cbe814f2d (1 event: retry×1 — on mcp__ost-agent__ost_ingest_inbox itself, same shape as the fee7afb0 citation above)
