---
type: Opportunity
status: unvalidated
source: 'USAGE:2026-07-26'
created: '2026-08-02'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion

A machine-recorded day of tool use: 93 invocations, 31 succeeded, 62 failed. No narrator selected or summarized those numbers — they are counted from the append-only invocation trace. The failures are not exotic. They are `no such node: probe`, `no such node: x`, and a create call rejected for carrying the literal string `undefined` where an evidence class belonged.

What that pattern describes is an agent working by probe: it cannot ask what exists, so it calls and reads the refusal. Every question about the tree's state costs a failed write to discover. The refusals are well-written and arrive too late to be cheap, and the trace cannot tell a genuine mistake apart from reconnaissance conducted through the error channel.

The contrast makes the point rather than the raw number. The preceding day recorded 108 calls on the same surface with zero failures, so this is not a broken tool — it is what happens when a session has to establish the shape of the tree before it can act on it.

**The need:** I want to find out what exists before I spend a call on it, instead of learning it from what the call refuses.

More than one way to address this: return existence and shape from a cheap read before any write, make refusals name the near-misses so one failure resolves the question, let a call be validated without being committed, or expose the tree's index directly so probing is unnecessary.

## Provenance

Distilled from `USAGE:2026-07-26` — a mechanical rollup of the tool-invocation trace, computed rather than composed. Contrast drawn from `USAGE:2026-07-25` (108 calls, 0 failed), which is left unmapped on purpose: a clean day reveals no need of its own.

**Recorded at `assertion`, and the reason is worth a human's attention.** This node rests on the most mechanical evidence the vault holds — a counted trace with no narrator anywhere in it — but the ladder grants `observed` only to provenance shaped like `TRANSCRIPT:…`, so a `USAGE:` source cannot claim it. A transcript record, which is a model's reading of a session, outranks a raw machine count. That looks like the ceiling tracking the channel's name rather than whether something was actually measured.
