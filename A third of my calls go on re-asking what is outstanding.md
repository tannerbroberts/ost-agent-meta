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
