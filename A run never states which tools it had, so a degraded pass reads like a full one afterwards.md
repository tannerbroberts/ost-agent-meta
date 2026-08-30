---
type: Opportunity
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — split from the bucket that held these solutions
  directly
evidence: assertion
authorship: machine
---
#Opportunity #unvalidated #evidence/assertion
[[A run declares the tools it needs and halts loudly when they are absent]]
[[Every run records the tool surface it actually had]]
[[A degraded pass has its own name and is not allowed to report a clean run]]

The tool surface varies by host and nothing records which one a given run got. A pass that quietly lacked half its tools produces a report indistinguishable from a complete one, so the failure is invisible at exactly the moment it should be loudest.

## Corroborating evidence — session friction transcripts (mapped 2026-08-16)

`TRANSCRIPT:030e5db3-9414-441f-9221-b4a984c11825` (9 friction events, tool_error×4/retry×5): four of the tool_errors are permission-denied on tools this pass's surface never had (`Glob`, `mcp__ost-agent__ost_flag_humans_required`, `mcp__ost-agent__ost_check`, `mcp__ost-agent__ost_status`) — the session discovered its degraded tool surface one denied call at a time, mid-pass, rather than being told up front which tools it actually held. Same need as this node's own prose. Evidence class: observed behavior, self-reported from the agent's own session transcript; grounds usability, not demand.

Several other unmapped `Session friction <id>` transcript records (e.g. `TRANSCRIPT:00908faf-a23c-4c02-a792-9c402a4df8ac`) show the same shape in miniature (a single denied/failed call with no prior warning of what the run did and didn't have). The transcript harvester currently emits one record per session with a raw event list rather than grouping by signature, so this pattern likely recurs across a large share of the ~200 still-unmapped `Session friction` records; the proposed solution "Cluster friction records by signature before the queue sees them" (elsewhere in this tree) would make signatures like this one countable instead of requiring a body read per session. Left uncounted here rather than guessed.

## The pre-declaration works, measured against a firing that lacked it (2026-08-30)

Recorded because it is a before/after on a shipped mitigation with a named control, not a restatement of the need.

**The control.** `TRANSCRIPT:030e5db3` — a firing on this vault — carries 9 friction events, and 4 of its `tool_error`s are permission denials on tools it did not hold: `ost_flag_humans_required`, `ost_check`, `ost_status`, and a `Glob` read grant on the product repo. That firing discovered its own surface by being refused, one call at a time. `TRANSCRIPT:59ee707b`, captured this pass, shows the same shape in miniature: a `Glob` denied on `/Users/tanner/dev/OST-Agent/test` by a firing that nonetheless held `ost_read_repo` and could reach the same directory through it.

**The treatment.** This firing's own prompt opened with two generated blocks — a `CORRECTIONS ALREADY ISSUED IN THIS WORKSPACE` list of previously-refused call forms, and a `What this surface withholds` list naming `ost_check`, `ost_debt`, `ost_deposit`, `ost_flag_humans_required`, `ost_gate`, `ost_rank_source` and `ost_status` as denied on purpose, with the note that a denied call is silent rather than refused with a message.

**The result.** This pass spent **zero** calls discovering its own surface. It did not call a withheld tool, and where it wanted one — `ost_flag_humans_required`, for six solutions whose tests are genuinely humans-required — it routed the request into its report rather than into a denial. The four wasted calls in the control are the measured cost the declaration removes.

**Why this bears on the need rather than merely on the mitigation.** The opportunity says a run never states which tools it had, so a degraded pass reads like a full one *afterwards*. This shows the same information has a second and cheaper use *beforehand*: a pass told its surface up front does not spend anything finding out, which is a saving the post-hoc labelling candidate beneath this node does not capture. Whoever ideates further here should treat pre-declaration and post-hoc disclosure as two positions on *when*, not as one solution — they solve different halves and this firing only exercised the first.

**What it does not establish.** n is one treated firing against two controls, all from this vault's own loop, and the pass was not blinded to the hypothesis — it read the withholds block and then reported on having obeyed it. It says nothing about whether the *report* this pass produces is legible as degraded to a later reader, which is the half the opportunity is actually about and which no firing can check on itself.

_Source: this firing's own prompt preamble and its own call record, plus `TRANSCRIPT:030e5db3` and `TRANSCRIPT:59ee707b` served by `ost_next_work`. Observed behaviour of this product; grounds usability, not desirability. No test was run and no result is recorded._
