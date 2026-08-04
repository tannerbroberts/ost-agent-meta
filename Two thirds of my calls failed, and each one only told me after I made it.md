---
type: Opportunity
status: unvalidated
source: 'USAGE:2026-07-26'
created: '2026-08-02'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[Publish the preconditions of every call so they can be checked before it is made]]
[[The refusal states the value that would have worked, not just the one that did not]]
[[A cheap validating call the caller may make before committing to the real one]]

A machine-recorded day of tool use: 93 invocations, 31 succeeded, 62 failed. No narrator selected or summarized those numbers — they are counted from the append-only invocation trace. The failures are not exotic. They are `no such node: probe`, `no such node: x`, and a create call rejected for carrying the literal string `undefined` where an evidence class belonged.

What that pattern describes is an agent working by probe: it cannot ask what exists, so it calls and reads the refusal. Every question about the tree's state costs a failed write to discover. The refusals are well-written and arrive too late to be cheap, and the trace cannot tell a genuine mistake apart from reconnaissance conducted through the error channel.

The contrast makes the point rather than the raw number. The preceding day recorded 108 calls on the same surface with zero failures, so this is not a broken tool — it is what happens when a session has to establish the shape of the tree before it can act on it.

**The need:** I want to find out what exists before I spend a call on it, instead of learning it from what the call refuses.

More than one way to address this: return existence and shape from a cheap read before any write, make refusals name the near-misses so one failure resolves the question, let a call be validated without being committed, or expose the tree's index directly so probing is unnecessary.

## Provenance

Distilled from `USAGE:2026-07-26` — a mechanical rollup of the tool-invocation trace, computed rather than composed. Contrast drawn from `USAGE:2026-07-25` (108 calls, 0 failed), which is left unmapped on purpose: a clean day reveals no need of its own.

**Recorded at `assertion`, and the reason is worth a human's attention.** This node rests on the most mechanical evidence the vault holds — a counted trace with no narrator anywhere in it — but the ladder grants `observed` only to provenance shaped like `TRANSCRIPT:…`, so a `USAGE:` source cannot claim it. A transcript record, which is a model's reading of a session, outranks a raw machine count. That looks like the ceiling tracking the channel's name rather than whether something was actually measured.

## Issues
- 2026-08-02 Ladder question raised while creating this node, for a human to rule on. `ost_set_evidence`/`ost_create_node` refused `observed` here because the ceiling for that rung requires provenance shaped like `TRANSCRIPT:…`, and this node cites `USAGE:2026-07-26`. But the usage channel is a counted, append-only trace of tool invocations with no narrator at any point, whereas a transcript record is a reading of a session. On the stated principle — that the measurement rungs assert something was actually measured — the usage channel appears to have at least as strong a claim to `observed` as the transcript channel, and possibly stronger. If that is right, the fix is in the ceiling rule rather than in this node, and every future node resting on a usage trace will be understated the same way. Recorded at `assertion` in the meantime, which understates it.

## Second clean day, dispositioned — unattended sweep, 2026-08-02 (sixth pass)

`USAGE:2026-07-27` (16 calls, 16 ok, 0 failed, all on the `cli-tool` surface) is the one evidence item outstanding this pass that carried no disposition anywhere in this vault. It is dispositioned here, by the same ruling this node's Provenance section already made for `USAGE:2026-07-25`: **a clean day reveals no need of its own**, and it stays unmapped on purpose rather than by oversight.

It does sharpen the contrast this node rests on, so it is worth one line. Three usage traces are now on record — `2026-07-25` (108 calls, 0 failed), `2026-07-27` (16 calls, 0 failed) and `2026-07-26` (the two-thirds-failed day this node is distilled from). The failure is not spread thin across the week; it is concentrated in a single day, with clean days either side. Whatever produced it was a condition of that day, not a background rate, which is a materially different thing to build against and is the sort of shape a summary would have flattened.

_Provenance: `USAGE:2026-07-27`, read in full this pass. Acknowledged with a reason, no node created — the affordance that would let this clear the counter is [[Let a pass mark evidence acknowledged, with a reason, without inventing an opportunity]], still unbuilt._

## The fourth trace, and it sharpens rather than repeats — unattended sweep, 2026-08-03

`USAGE:2026-08-02` is now on record: **240 tool invocations, 235 ok, 5 failed** across 8 sessions, p50 2ms. All 240 on the `mcp` surface. That is a **2% failure rate**, against this node's 67%.

The four traces now read: `2026-07-25` 108 calls / 0 failed, `2026-07-26` 93 / 62, `2026-07-27` 16 / 0, `2026-08-02` 240 / 5. The Provenance section above argued the 67% day was *a condition of that day, not a background rate*. A 240-call day at 2% is the strongest confirmation of that reading available — an order of magnitude more work, essentially none of it spent on reconnaissance.

**But the five failures are the interesting part, because they are all the same failure.** All three shown are `ost_create_node` refused with the same rule:

> `"…" cannot declare 'stated': it cites channel:inbox, which has earned 'assertion' — and 'stated' is the ceiling for a channel. A report is ranked by the channel it arrived on, never by what the report says about itself`

Three named nodes — *"A recorded failure can't be reproduced, because the record omits where it ran"*, *"Having the vault is not the same as having the tools, and nothing points that out"*, *"A scheduled run finds out its tools are missing only after it has started"* — each refused for the identical reason, in one day, on one surface. So the residual 2% is not scattered noise. It is **one unlearned rule, paid for five times**, which is this node's need exactly: the ceiling a source can support is a fact the agent could have been told before composing, and instead learned from what the call refused. It is also [[The same refusal is rediscovered every session, because nothing carries the lesson forward]], now demonstrated inside this product rather than in the shell around it.

**A note for whoever rules on the Issue above.** That Issue argues the `USAGE:` channel is understated at `assertion`. This trace is a further instance of the same asymmetry: it is a counted, unnarrated record of 240 invocations — including the verbatim text of the refusals — and it still cannot rise above the floor. Recorded, not decided.

_Provenance: `USAGE:2026-08-02`, read in full this pass. Dispositioned here rather than mapped to a node of its own, by the same ruling this node already applied to `USAGE:2026-07-25` and `USAGE:2026-07-27`; the affordance that would let a pass clear the counter honestly is still [[Let a pass mark evidence acknowledged, with a reason, without inventing an opportunity]], still unbuilt._

## Corroboration — two more refusals learned the same way (unattended sweep, 2026-08-03)

Both `tool_error` events in `TRANSCRIPT:3d729ebc-348f-4d45-8f3c-25df1de8fbc9` have this node's shape — a rule that existed the whole time, discovered by tripping over it:

- `Blocked: sleep 45 followed by: gh run list … gh pr view 33 …` — a compound command refused by policy. Nothing told the session the composition was disallowed until it had composed it.
- `/Users/tanner/.local/bin/ost-reports: line 21: mapfile: command not found` — a script that assumes a shell builtin the running shell does not have. Reported at line 21, after the first twenty lines had already run.

Neither is a hard case. Both are knowable in advance and neither was knowable in advance *to the agent*, which is the whole claim: the cost is not that the calls failed, it is that the failure was the only channel through which the constraint was ever communicated.

_Source: `TRANSCRIPT:3d729ebc-348f-4d45-8f3c-25df1de8fbc9`, read in full this pass — observed behavior from the agent's own transcript. Grounds usability, not demand. Corroboration only; the node's rung is unchanged._

## Four more instances, and this time the refusal came from the harness rather than from this tool

Read this pass from the transcript channel. All four have the node's shape — a constraint that was knowable in advance and was not knowable in advance *to the caller*:

- `TRANSCRIPT:785ea509-…` — `Monitor` refused with `InputValidationError: … An unexpected parameter 'timeout' was provided`. The parameter was invented by the caller because the tool's schema was not in hand at the moment of composing the call.
- `TRANSCRIPT:4ff7b605-…` and `TRANSCRIPT:516fdfb8-…` — `Workflow` refused twice, in two separate sessions, with `Script parse error: Unexpected token`, and both times the error volunteered the cause: *"Workflow scripts must be plain JavaScript — common causes are TypeScript syntax (type annotations, interfaces, generics)"*. The script had to be written in full and submitted before anything said which dialect it had to be in.
- `TRANSCRIPT:fd2c6d71-…` and `TRANSCRIPT:516fdfb8-…` — `CronList` and `TaskOutput` re-issued with byte-identical arguments (`TaskOutput` three times on `task_id: w1ruwr8ip`). Not refusals, but the same underlying gap read from the other side: nothing distinguished "this returned nothing because there is nothing" from "this returned nothing yet".

**Why the `Workflow` pair is the sharpest of the four.** The cost is proportional to the work discarded, and a workflow script is the largest single artifact in this list — one of the two failures reports the token at line 172. A refusal that arrives at submission time charges the full price of composing the thing before saying which language it should have been in. The `Monitor` case charges one call; this charges a script.

**The generalisation, which is new to this node.** Every instance recorded here before now was a refusal issued by `ost-agent` itself — its own ladder ceilings, its own `no such node`. These four come from the surrounding harness, and they behave identically. That matters for scoping any fix: [[Publish the preconditions of every call so they can be checked before it is made]] can only ever cover this product's own surface, so it would have caught none of these four. Whatever fraction of the cost lives outside this tool's calls is outside what this tool can publish preconditions for — and on this pass's sample that fraction is all of it.

**What it does not establish.** Four events across five sessions, with no denominator: the transcript channel captures friction, not totals, so nothing here supports a rate. The claim is about the shape, not the frequency.

_Provenance: five friction records from the transcript adapter, machine-captured, no narrator. Observed behavior of this product's own agent; grounds usability, not desirability. Corroboration only; the node's rung is unchanged. Unvalidated — for human review._
