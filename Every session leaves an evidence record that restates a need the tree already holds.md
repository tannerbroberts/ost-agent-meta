---
type: Opportunity
source: 'TRANSCRIPT:03a79a59-682a-4528-83c6-4c39d8c658ef'
created: '2026-08-06'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed
[[Let a friction record corroborate an existing opportunity instead of demanding a new node]]
[[Cluster friction records by signature before the queue sees them]]

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
