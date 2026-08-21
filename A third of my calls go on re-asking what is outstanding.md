---
type: Opportunity
source: 'USAGE:2026-08-02'
created: '2026-08-03'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[The sweep returns a version, and re-asking an unchanged tree costs nothing]]
[[Each write returns the delta it caused, so the sweep updates in the caller's hands]]
[[One sweep per pass by contract, and a pass that re-reads must say what changed]]

I pay for every call the agent makes, and a third of them are it asking the tree what still needs doing — a question it already asked, and got a full answer to, a few calls earlier. Nothing it learned from that answer survived long enough to spend it.

## What the evidence shows

`USAGE:2026-08-02` — 240 tool invocations, machine-recorded, across 8 sessions:

| Tool | Calls | Share |
| --- | --- | --- |
| ost_create_node | 94 | 39% |
| ost_next_work | 82 | 34% |
| ost_append_to_node | 18 | 8% |
| ost_annotate | 18 | 8% |
| ost_ingest_inbox | 15 | 6% |
| ost_read_tree | 6 | 3% |
| ost_set_evidence | 5 | 2% |
| ost_status | 2 | 1% |

`ost_next_work` is a read-only orchestration call: it changes nothing, and it returns the same sweep until something else changes it. 82 of them against 94 writes is close to one full re-read of the outstanding list per write performed. The comparison days make the shape clearer rather than dismissing it as volume: `USAGE:2026-07-25` ran 17 `ost_next_work` against 32 creates and 25 appends, and `USAGE:2026-07-27` ran none at all against 16 writes.

## What I actually want

To read the outstanding list once, hold it, and spend the rest of the budget acting on it — and to re-read only when something I did could plausibly have changed it.

## What this does not claim

The trace records what was called, not why. A call that re-reads the sweep after a batch of writes is legitimate confirmation, not waste, and the trace cannot tell the two apart. What it does establish is the ratio, and that the ratio moved sharply between 25 July and 2 August.

## On the rung this node carries

This node rests on `assertion`, which is the weakest rung and lower than the evidence deserves. That is not modesty — it is a refusal. `ost_set_evidence` declined `observed` here on the grounds that the source is not itself a recording, and the ladder recognises only `TRANSCRIPT:` provenance as one. The `USAGE:` channel describes itself, in the body of every record it emits, as a "mechanical rollup of the append-only tool-invocation trace, computed, not composed: no agent narrated, selected, or summarized these numbers." Whether a machine-recorded invocation trace should be a recording for ladder purposes is a question for a human, not something this pass may decide by talking the node upward. Flagged rather than worked around.

Evidence class: observed behaviour — machine-recorded trace of tool invocations, no narrator. It grounds usability and the agent-tool loop, not external demand.

## Issues
- 2026-08-03 Evidence-ladder mismatch, for a human to rule on. This node cites `USAGE:2026-08-02` and rests on `assertion`, because `ost_set_evidence` refused `observed` — the ladder recognises only `TRANSCRIPT:` provenance as a recording. But every `USAGE:` record states in its own body that it is a "mechanical rollup of the append-only tool-invocation trace. Computed, not composed: no agent narrated, selected, or summarized these numbers," and closes by declaring its own evidence class as "observed behavior — machine-recorded trace of tool invocations; no narrator." So the channel asserts it is a recording and the ladder ranks it as a claim from inside the building. One of the two is wrong. This pass took the refusal at face value and declared the weaker rung rather than routing around it, which is the correct behaviour under the rules but leaves a real measurement carrying the floor rung. A human should decide whether `USAGE:` earns recording status alongside `TRANSCRIPT:`; if it does, every node sourced from a usage trace is currently understated.

## Corroborating usage traces (machine-recorded, no narrator)

- `USAGE:2026-08-03` — 312 calls across 6 sessions: `ost_create_node` 237, `ost_next_work` 39, `ost_append_to_node` 15, `ost_ingest_inbox` 11, `ost_annotate` 6, `ost_read_tree` 4. p50 duration 1ms.
- `USAGE:2026-07-25` — 108 calls across 3 sessions: `ost_create_node` 32, `ost_append_to_node` 25, `git_commit` 19, `ost_next_work` 17, `ost_annotate` 7, `ost_read_tree` 7.

These two traces qualify the claim in this node's title rather than simply confirming it, and the correction is worth keeping. On 2026-08-03 the re-asking calls (`ost_next_work` + `ost_read_tree` = 43) are **14%** of the day, not a third, because that day was dominated by a large ideation burst. On 2026-07-25 the same two are **24 of 108, 22%**, against a much smaller write volume. So the fraction is not a constant — it rises as the ratio of writing to orienting falls, which means the cost lands hardest on exactly the passes that have little to write, i.e. the maintenance passes this loop runs most often.

One further datum from `USAGE:2026-08-03`: the single failed call of 312 was an `ost_create_node` refused for declaring `observed` on a node whose sources support only `assertion` — the ladder's ceiling doing its job, and evidence that the refusal path is exercised in practice rather than theoretically.

Evidence class is observed behaviour — a machine-recorded trace of tool invocations. It grounds the agent-tool loop, not external demand.

## Corroboration — the fraction, measured (2026-08-04 sweep)

Two machine-recorded usage traces now put a number on this node's title, and the number is the one the title guessed.

USAGE:2026-08-04 — 356 calls across 5 sessions:

| Tool | Calls | Share |
| --- | --- | --- |
| ost_append_to_node | 119 | 33% |
| **ost_next_work** | **111** | **31%** |
| ost_set_instrument | 88 | 25% |
| ost_ingest_inbox | 15 | 4% |
| ost_create_node | 14 | 4% |

USAGE:2026-08-03 — 312 calls across 6 sessions: `ost_next_work` 39 of 312 (13%), against `ost_create_node` 237 (76%).

So the fraction is not constant — it swung from 13% to 31% between two consecutive days — and the swing is informative. The 08-03 pass was creating nodes in bulk, where one sweep answers many writes. The 08-04 pass was setting instruments one at a time, where the sweep has to be re-asked to find out which solution is next, because the list it returns is capped at 25 of 164 and shifts under you as you work it. **The re-ask rate tracks how granular the work is**, and instrument work is the most granular kind the tree has.

That points at a cheaper fix than caching: the sweep is re-asked not because its answer went stale but because its answer was truncated. A caller working a 164-item backlog through a 25-item window must return to the window six times to see the backlog once.

_Note on the ladder: this node still rests on `assertion` and this append does not change that. An attempt to raise it to `observed` was refused on 2026-08-03 — recorded in that day's trace as the only failed call of 312 — because the rung is capped by what the node's own `source` points at, and appending a measurement to the body does not move it. Raising it would mean a node sourced from the recording, which is a human's call._

_Recorded as corroboration during the 2026-08-04 unattended pass. USAGE:2026-08-03 and USAGE:2026-08-04 remain unmapped in the sweep. Observed behavior, mechanically captured; grounds usability, not demand._

## A sharper cause, observed this pass — evidence cited in prose isn't recognised as mapped (2026-08-17 unattended sweep)

Two `unmappedEvidence` items this pass (`INBOX:2026-07-24-friction-a-backgrounded-session-leaves-no-marker-of-where.md` and `INBOX:2026-08-16-build-loop-stuck-ask-the-open-question-first-and-offer-options-only-once-the-.md`) were read in full and found already thoroughly incorporated — the first cited three separate times in "A run that dies while I am away stays dead, and nothing says where it stopped"'s body (2026-08-15, 2026-08-16, and once more, unlabeled), the second fully accounted for in "Ask the open question first, and offer options only once the frame is agreed"'s own `## History` with the exact numbers from the evidence body. Neither is stale work; both are the tree correctly reflecting evidence a human or prior pass already read. But `ost_next_work` still lists both as unmapped, which means its detector checks a node's `source` field (singular) rather than whether the evidence id appears anywhere in a node's body/History. This is a distinct mechanism from the truncation cause identified 2026-08-04 above, and it compounds it: some share of every pass's `unmappedEvidence` re-reads and re-confirms work that is already done, rather than genuinely new work. A human should decide whether the detector should also match citations in prose, or whether nodes that fully incorporate an evidence id should record that fact somewhere the detector reads.

## Corroboration — single-node reads now dominate, not sweep re-asks (2026-08-18 unattended sweep)

`USAGE:2026-08-18` — 580 calls across 19 sessions, 0 failed:

| Tool | Calls | Share |
| --- | --- | --- |
| ost_read_tree | 277 | 48% |
| ost_next_work | 143 | 25% |
| ost_create_node | 55 | 9% |
| ost_append_to_node | 45 | 8% |
| ost_ingest_inbox | 38 | 7% |
| ost_read_repo | 21 | 4% |
| ost_annotate | 1 | <1% |

`ost_next_work` sits at 25% today — close to the "third" the title names, within the range this node's own corroborations already show swinging 13%–34%. The new datum is `ost_read_tree` at 48%, now the single largest share of the day and nearly double `ost_next_work`. `ost_read_tree` did not exist as a per-node body read until the 2026-08-17 tool change recorded on "The repair I am asked to make requires rewriting prose no tool will show me" (a `node` parameter added so a single call returns one node's full prose before an edit/merge/append). This day's trace is the first full-day usage record since that change, and it suggests the re-asking cost this node describes has partly migrated: rather than re-calling the sweep to recover context, sessions now call `ost_read_tree({node})` once per node touched — a cost the sweep-re-ask framing above does not price in, because it is a different tool answering a related but distinct question ("what does this node say" rather than "what is still outstanding").

Evidence class: observed behaviour — machine-recorded trace of tool invocations, no narrator. Grounds usability and the agent-tool loop, not external demand.

## The 2026-08-17 mechanism, now with a number on it (unattended sweep, 2026-08-21)

The section above identified the cause and could not size it: `unmappedEvidence` matches on a node's `source` field, so evidence fully incorporated into a node's *body* still reads as unmapped forever. Today's sweep measures the consequence.

`ost_next_work` reported **357 unmapped evidence items, with `agedOutEvidence.count: 0`** — nothing has ever aged out of this queue. All 357 are from the `transcript` channel. This pass read six of them in full, sampling the largest bodies (the ones most likely to carry an unmapped need): every one described friction already mapped — permission refusals on withheld tools, "File has not been read yet", malformed-JSON `Read` retries, exit-143 timeouts. One (`TRANSCRIPT:09ec7cd2-…`, the three consecutive `HTTP 503` errors from api.github.com) is not merely already-mapped but already **cited twice** in the body of "A test that failed because the machine was busy looks exactly like one that failed because I broke something" — once as a dated corroboration section and once as an "Additional observed instance". It is still listed as unmapped.

So the queue is not a backlog of unread evidence. It is a backlog of *already-read* evidence that the detector cannot see has been read, and it grows monotonically because nothing retires an item and nothing ages one out. Two costs follow, and the second is the expensive one:

- Every sweep re-reads some share of it to find out it is already done — the re-asking cost this node is about.
- The genuinely new record is indistinguishable from the 356 repeats. This pass could only find the novel ones by reading bodies one at a time, and at 357 items that is not a strategy any sweep can afford. A channel with no novelty signal and no age-out converges on being unreadable.

**For a human:** the repair named on 2026-08-17 — match citations in prose, or let a node record which evidence ids it has incorporated — is unchanged, and now has a size. A cheaper partial: age-out or a novelty diff would restore a readable queue without touching the detector.

_Measured from this pass's own `ost_next_work` response. Observed behaviour of the tool, not an outside report; rung unchanged at the floor for the reason this node already records._
