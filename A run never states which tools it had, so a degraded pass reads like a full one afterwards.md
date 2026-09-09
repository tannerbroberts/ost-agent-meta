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

## 2026-09-09 — the pre-declaration failed in a new way: two declarations in one prompt disagreed, and the pass had to spend a call to find out which was true

Kept short. This is a counter-observation to the section above, not a restatement of it — that section measures the declaration working; this one records the first observed instance of it working against itself.

**What happened.** This firing's prompt carried the same two generated blocks the 2026-08-30 section names, and the `What this surface withholds` list named seven tools — `ost_check`, `ost_debt`, `ost_deposit`, `ost_flag_humans_required`, `ost_gate`, `ost_rank_source`, `ost_status` — and did **not** name `ost_read_repo`. Elsewhere in the same prompt, the hard-rules paragraph asserted the opposite in prose: "This unattended sweep holds no outward-sensing grant on purpose — `ost_search_web` / `ost_read_web` / `ost_read_repo` stay on the attended path." The two declarations are about the same surface and cannot both be right.

**Which was true, and what settling it cost.** The withholds list was right. `ost_read_repo` is granted: this pass listed `test/` (31 entries), `test/friction/` and `test/adapters/` through it without difficulty. Settling it took one speculative call — the exact cost the 2026-08-30 section credits the pre-declaration with removing. The saving that section measured is real, and it is conditional on the declarations agreeing.

**Why this is a need and not a typo.** The failure direction is the expensive one. A pass that believed the prose would hold repo sight and decline to use it, and the work it would decline is named in this vault's own `ost.config.yaml`: the `product.repos` key was set on 2026-08-09 because "six consecutive discovery passes reported repo sight dead and declined to instrument 62 prose-only tests rather than write instruments against invented paths." That is the same refusal, with a measured cost, caused last time by an absent grant and this time available to be caused by a sentence. This node's prose says a degraded pass reads like a full one; this is the inverse and it is not covered by that wording — **a full pass reads like a degraded one, to itself, while it is running.** The three candidates beneath this node all assume the run's surface is the thing in question; here the surface was fine and its description was not, so none of them fires.

**A cheap repair exists and is not this pass's to make.** The withholds block is generated from the run's actual grant; the contradicting sentence is hand-written prompt prose. Deleting the three tool names from that sentence would remove the contradiction at its source, and is the operator's call on the firing prompt, which is not in `product.repos` and is not reachable from this surface.

**Limits.** One firing, this vault's own loop, and the observation cannot be separated from the pass that made it — the same non-blinding this node's 2026-08-30 section names about itself. It is a first-party read of a prompt, not of any mechanism that generates one, so nothing here establishes how the contradiction arose or whether it recurs; a second instance would be needed to call it a class rather than an event. No claim is made that the prose sentence is wrong on the two web tools — neither `ost_search_web` nor `ost_read_web` was called, so their grant is untested and this records only the `ost_read_repo` disagreement. Nothing was executed, no rung moved, no instrument set, no status changed, no node created. `ost_check` is withheld on this surface, so this write is unverified by the invariant checker by design.

_Source: this firing's own prompt preamble, its own call record, and `ost.config.yaml` read first-party. Observed behaviour of the surface this agent runs on; it grounds usability, not desirability._
