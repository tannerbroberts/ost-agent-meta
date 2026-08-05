---
type: Solution
status: unvalidated
source: >-
  founder-directive:2026-07-24 — assertion-vs-trace distinction, stated in
  session
created: '2026-07-25'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Transcripts already contain every call an in-band trace would have recorded]]

**The idea.** The adopt-existing lane this tree was missing: Claude Code transcripts already contain every tool_use block with arguments and results — a mechanical trace nobody instruments. Extend the existing transcript harvester to emit per-session invocation statistics instead of (only) distilled friction events, and the trace channel exists with zero new product surface.

**Contrast with siblings:** cheapest to build and richest per event (full args, full results), but blind to MCP-driven and headless pass usage, dependent on transcript format stability, and gated on quietMinutes latency. The in-band trace (sibling) covers all surfaces with size-only privacy; this covers one surface with full fidelity.

**Trade-off:** full-content traces raise the privacy bar exactly where the size-only design deliberately ducked it.

## Definition of done

"Check transcript-derived call parity against the in-band trace for one session"

```
npx vitest run test/telemetry/transcript-trace-parity.test.ts
```

Green means the transcript carries the same calls the in-band trace does, which is the whole premise of dropping the second instrument. It does not settle the cases where the two would legitimately diverge — a call the harness made that never reached a transcript, or a session that ended without one — so parity on one session is a floor, not a licence to remove anything.

## History
- 2026-08-05 unlinked "Check transcript-derived call parity against the in-band trace for one session" — moved under "Transcripts already contain every call an in-band trace would have recorded" — the belief this test measures now has a node of its own
