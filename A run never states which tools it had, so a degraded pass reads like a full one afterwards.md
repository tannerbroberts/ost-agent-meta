---
type: Opportunity
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — split from the bucket that held these solutions
  directly
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[A run declares the tools it needs and halts loudly when they are absent]]
[[Every run records the tool surface it actually had]]
[[A degraded pass has its own name and is not allowed to report a clean run]]

The tool surface varies by host and nothing records which one a given run got. A pass that quietly lacked half its tools produces a report indistinguishable from a complete one, so the failure is invisible at exactly the moment it should be loudest.

## Corroborating evidence — session friction transcripts (mapped 2026-08-16)

`TRANSCRIPT:030e5db3-9414-441f-9221-b4a984c11825` (9 friction events, tool_error×4/retry×5): four of the tool_errors are permission-denied on tools this pass's surface never had (`Glob`, `mcp__ost-agent__ost_flag_humans_required`, `mcp__ost-agent__ost_check`, `mcp__ost-agent__ost_status`) — the session discovered its degraded tool surface one denied call at a time, mid-pass, rather than being told up front which tools it actually held. Same need as this node's own prose. Evidence class: observed behavior, self-reported from the agent's own session transcript; grounds usability, not demand.

Several other unmapped `Session friction <id>` transcript records (e.g. `TRANSCRIPT:00908faf-a23c-4c02-a792-9c402a4df8ac`) show the same shape in miniature (a single denied/failed call with no prior warning of what the run did and didn't have). The transcript harvester currently emits one record per session with a raw event list rather than grouping by signature, so this pattern likely recurs across a large share of the ~200 still-unmapped `Session friction` records; the proposed solution "Cluster friction records by signature before the queue sees them" (elsewhere in this tree) would make signatures like this one countable instead of requiring a body read per session. Left uncounted here rather than guessed.
