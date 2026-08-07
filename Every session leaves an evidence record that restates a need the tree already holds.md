---
type: Opportunity
source: 'TRANSCRIPT:03a79a59-682a-4528-83c6-4c39d8c658ef'
created: '2026-08-06'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed
[[Let a friction record corroborate an existing opportunity instead of demanding a new node]]
[[Cluster friction records by signature before the queue sees them]]
[[Record a read-and-skipped judgement so the queue drains without a write]]

**The need.** I turned on self-observation so my own usage would improve the tool. What I got is a queue that grows by one record per session, where most records say something the tree already knows — and the only way to take one off the queue is to create a node, so honest maintenance makes the tree worse.

**What was observed.** This pass opened with 65 unmapped evidence items. Every one is a `TRANSCRIPT:` session-friction record. Read in full, they resolve to a small set of frictions the tree has already named:

| What the record shows | Where the tree already holds it |
|---|---|
| Denied permissions for tools the skill declares (`Glob`, `ost_check`, `ost_status`, `ost_debt`, `ost_flag_humans_required`) | "The agent has to guess what resources it's actually working with"; "A sweep that cannot read its subject reports a clean result" |
| `Edit` refused — "File has not been read yet" | "The file changed after I read it, and the failed edit is how I find out" |
| An unattended firing raising `AskUserQuestion` with nobody watching | "The work I most want to run unattended is the work that keeps needing a decision"; "The whole loop waits on one human command, and nobody is told it is waiting" |
| Repeated `retry` of `ost_next_work` / `ost_ingest_inbox` | "The same refusal is rediscovered every session, because nothing carries the lesson forward" |

Source record for this node — session `03a79a59`, 15 friction events, 9 tool errors and 6 retries — is entirely the first and fourth rows.

**Why the obvious answers are both wrong.** Mapping each record to a new Opportunity would add 65 nodes restating four needs, to a tree already carrying 121 opportunities; that is the duplicate debt the merge tooling exists to pay off, created deliberately. Ignoring them leaves `done: false` permanently, so the pass can never report completion and the operator can never tell when to stop paying. The queue as built admits no third option, and the skill's own instruction — "if an item reveals no genuine need, skip it" — has no mechanism behind it: there is no way to record that an item was read and judged redundant.

**Why this is a need and not a complaint about a tool.** The operator asked for their usage to feed back automatically. The channel delivers volume, not learning. What they want from a self-observation channel is the fourth occurrence of a friction to make its opportunity *more believable*, not to make a sixty-fifth node.

**Litmus test.** More than one way to address it: cluster records before they reach the queue, let a record attach to an existing opportunity as corroboration instead of demanding a new node, or record a read-and-skipped judgement so the queue drains without a write.

⚠️ Unvalidated. Distilled from the tree's own instrumentation by the agent that generated the transcripts, so it is well-grounded on what happened and not grounded at all on what an operator would want done about it. Evidence rung `observed` covers the friction records' existence and content, captured mechanically; it does not cover the claim that a smaller queue is preferable, which is nobody's stated preference yet.

## Corroboration — the queue is growing, not draining — 2026-08-07

This node was written on 2026-08-06 against 65 unmapped evidence items. One day later the count is **73**, every one still a `TRANSCRIPT:` session-friction record, and the three solutions beneath this node are unbuilt. The rate is roughly 8 records a day and the queue has never gone down.

This pass read six of the new records in full and they land in the same four rows the table above already names. The dominant one is unchanged and is this vault's own instrumentation watching its own sweep fail: sessions `49d6b2d3` and `3b9eaea5` are almost entirely permission denials for `ost_flag_humans_required`, `ost_check`, `ost_status`, `ost_debt` and reads of the product directory — the tools this surface withholds. Session `3a54bb43` and session `bfa8808c` are three and three `Edit` refusals reading "File has not been read yet". Session `c0b41870` is a single `ost_next_work` retry.

One record carries something the table does not cover, and it is worth naming even though it is not a new need: session `bfa8808c` shows a stored probe firing — `Error: STALE RECORDING — "git-status-porcelain-v1-line-shape" no longer matches what its probe returns`. That is a guard working as designed, captured by the friction channel as though it were friction. Worth knowing because it means the channel's volume is not purely failure: some of what it collects is the product succeeding, and any clustering solution built under this node will have to tell those apart or it will file working mechanisms as pain.

**What this pass did with the 73, and why.** It mapped none of them. Creating a node for each would add 73 restatements of four known needs to a tree already holding 123 opportunities, which is the outcome this node exists to argue against; and the skill's sanctioned alternative — skip an item revealing no genuine need — still has no mechanism, so the skipped items stay on the queue and `done` stays false. That is not a decision this pass reached reluctantly, it is the same decision the 2026-08-06 pass reached, and the fact that two consecutive sweeps have declined to drain a queue they are instructed to drain is the strongest argument yet for building one of the three solutions below.

_Source records: `TRANSCRIPT:49d6b2d3-b867-4996-9d9d-8f10dd0871de`, `TRANSCRIPT:3b9eaea5-d098-4f47-ad0a-65871012d639`, `TRANSCRIPT:3a54bb43-2b44-46b3-8266-faca5115e2b0`, `TRANSCRIPT:516fdfb8-bab1-41a4-b1e5-92fde97bd90d`, `TRANSCRIPT:bfa8808c-0058-40f4-876e-c84eca8c1254`, `TRANSCRIPT:c0b41870-30c6-42d2-8110-0f46385af010`. Observed behavior from the agent's own transcripts; grounds usability, not demand. No rung change — these records corroborate this node's existing `observed` rung and do not lift it._
