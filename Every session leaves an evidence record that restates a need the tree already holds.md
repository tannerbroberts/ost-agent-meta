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

**The need.** Self-observation was turned on so the agent's own usage would improve the tool. What it produces is a queue that grows daily, where nearly every record restates a need the tree already holds — and the only way to take one off the queue is to create a node, so honest maintenance would make the tree worse (duplicate debt) rather than better.

**The four rows every session-friction record has landed in, across 20+ sweeps and a full corpus grep (2026-08-16):**

| What the record shows | Where the tree already holds it | Corpus count (2026-08-16) |
|---|---|---|
| `File has not been read yet` / `modified since read` / `String to replace not found` | "The file changed after I read it, and the failed edit is how I find out" | 173+16 occurrences / ~109 files |
| `requested permissions to read from …` (denied tool/path grants) | "The agent has to guess what resources it's actually working with"; "A sweep that cannot read its subject reports a clean result" | 56 occurrences / 49 files |
| An unattended firing raising `AskUserQuestion` with nobody watching | "The work I most want to run unattended is the work that keeps needing a decision"; "The whole loop waits on one human command, and nobody is told it is waiting" | — |
| Repeated `retry` of `ost_next_work` / `ost_ingest_inbox` | "The same refusal is rediscovered every session, because nothing carries the lesson forward" | — |

A fifth candidate shape — malformed tool calls, mangled tool names, zsh/shell syntax failures, i.e. the run getting the call itself wrong and finding out only after — was tracked separately across several sweeps and **closed on 2026-08-10**: it is not a fifth row here, it is "Two thirds of my calls failed, and each one only told me after I made it" issued by the harness. Route new instances there.

**Why the obvious answers are both wrong.** Mapping each record to a new Opportunity restates four known needs at scale (the queue passed 240 in August alone against a tree that started near 120 opportunities) — the exact duplicate debt `ost_merge_nodes` exists to pay off, created deliberately. Ignoring them leaves `done: false` permanently. The skill's own instruction — "skip an item revealing no genuine need" — has no mechanism behind it: there is no tool call that records "read and judged redundant" without either creating a node or growing this one. That gap is real product debt, not an oversight by any one pass.

**Litmus test (more than one way to address it).** Passes: cluster records by signature before the queue sees them; let a record corroborate an existing opportunity instead of demanding a new node; record a read-and-skipped judgement so the queue drains without a write. Candidate solutions for all three sit beneath this node, unbuilt.

**One standing item is not this channel's noise and won't clear from here.** `INBOX:2026-07-24-friction-a-backgrounded-session-leaves-no-marker-of-where.md` sits on the queue because a 2026-08-07 merge dropped its citing node's `source:` frontmatter; its actual need lives on "An interrupted run leaves no trustworthy account of what it completed." No tool on this surface can repair the mapping — it will reappear every pass until a human sets `source` directly or the merge tool is fixed to union it.

**Repo-succeeding events also arrive on this channel and must not be filed as friction.** A stale-recording guard firing, or a builder's pre-write existence check on a file it is about to create, both generate a friction-shaped record; a clustering solution has to tell "product failed" from "product worked as designed, verbosely."

⚠️ Unvalidated. Distilled from the tree's own instrumentation, so well-grounded on what happened and not at all on what an operator would want done about it. Evidence rung `observed` covers the friction records' existence and content; it does not cover the claim that a smaller queue is preferable, which is nobody's stated preference.

## History
- 2026-08-06 → 2026-08-17: 20 consecutive sweeps read new arrivals, confirmed each lands in a known row, and mapped none — trend 65 → 73 → 84 → 92 → 100 → 102 → 105 → 107 → 113 → 115 → 119 → 122 → 123 → 124 → 126 → 129 → 131 → 132 → 133 → 134 → 209 → 210 → 212 → **244** (2026-08-17). No new friction shape has been found since the fifth-row question closed on 2026-08-10. The queue has never gone down. Full per-sweep detail (session IDs, individual record reads, corpus-grep methodology) is preserved in git history on this node prior to this edit.
- 2026-08-17 body compressed (this edit) — 20 near-identical dated entries folded into the standing finding above; nothing dropped, see git log.
- 2026-08-17 body edited — 20 consecutive pass-entries (2026-08-06 through 2026-08-17) grew this node to 58KB, each reaching the identical conclusion — map none, queue does not drain — restated in full prose every time. Compressing to the standing finding plus a compact trend log, per the precedent already set on the Outcome node's 2026-08-04 edit ("each restated what the tree already knew structurally... git holds every one"). No claim is dropped; git history holds the full prior text.

## Issues
- 2026-08-17 The three solutions beneath this node remain unbuilt after 20 sweeps confirming the need. Building one of them — most likely "Record a read-and-skipped judgement so the queue drains without a write" — would end the pattern this History section now summarizes instead of restates.
