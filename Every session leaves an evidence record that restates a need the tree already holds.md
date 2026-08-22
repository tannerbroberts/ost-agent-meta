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
[[Have the transcript adapter emit one rolling record per friction shape instead of one per session]]

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

## Trend continued and the table extended — 2026-08-21 (unattended sweep)

Added as one entry rather than a prose restatement, per the 2026-08-17 Issues note. Two things this pass can add that the standing finding does not already carry.

**The trend, continued: 244 (2026-08-17) → 359 (2026-08-21).** Up 115 in four days, against roughly one-a-day growth over the preceding fortnight. The queue has still never gone down. Two of the 359 were captured by this pass's own `ost_ingest_inbox`; both are the read-before-write shape.

**Corpus counts re-measured over all 359 records** (grep over `.ost-agent/evidence/TRANSCRIPT_*.md`, so these cover the whole population and not the 25 the sweep displays):

| Shape | Occurrences / files | Row |
|---|---|---|
| `File has not been read yet` | 289 / 173 | row 1 |
| `requested permissions to read from …` | 82 / 69 | row 2 |
| `Blocked: sleep N followed by …` | 34 / 31 | **not in the table — see below** |
| `could not be parsed as JSON` | 24 / 19 | closed 2026-08-10, routes to "Two thirds of my calls failed, and each one only told me after I made it" |
| `exceeds maximum allowed size (256KB)` | 2 / 2 | homed on "More reaches my senses than fits in the window where I think" |

**A fifth row, and unlike the 2026-08-10 candidate it survives.** Thirty-four records across thirty-one sessions are the harness refusing a `sleep`: `Blocked: sleep 45 followed by: gh pr checks 18 | tail -10`, `sleep 90 followed by: echo done`, `sleep 120 followed by: tail -5 …`. The run has started something that takes minutes — a CI check, a background build-loop log, a backgrounded task — and has no permitted way to wait for it, so it reaches for `sleep` and is refused with a pointer to Monitor's until-loop.

This is not row 4. Row 4 is a run re-issuing a tool call after a transient failure; this is a run being told a whole *category* of waiting is unavailable to it, and it is not noise — the tree already holds it twice, as "The Monitor tool refuses the exact commands an unattended run needs to check on its own background work" and "My loop spends its time waiting for a check it cannot subscribe to". So the standing claim stands ("no new friction shape has been found") in the sense that matters — the tree holds it — but the table under-describes the channel, and a clustering solution built to the four rows would leave a thirty-one-session shape unclustered. Route new instances to the Monitor node.

**Nothing was mapped, for the reason this node exists.** Every one of the 359 lands in a row above, all of which are held. There is still no tool call on this surface that records "read and judged redundant" without either creating a duplicate node or growing this one — so this entry is itself an instance of the debt it describes, which is the third pass in a row that has had to say so.

_Method: `Grep` over the vault's own evidence sidecar, 2026-08-21, plus full reads of four representative records. First-party counts over stored records; no node was created and no rung moved._

## Addendum to the 2026-08-21 entry above — the channel split, and one standing claim that has cleared

Two facts the entry above does not carry. Kept to this length deliberately, per the 2026-08-17 Issues note.

**1. The backlog is one channel, entirely.** Counted on disk: `.ost-agent/evidence/` holds **458** records, of which **385** are `TRANSCRIPT_` and **73** are not (`INBOX_`, `USAGE_`, `INBOX_friction_`). The sweep reports **361 unmapped**, so **97 are mapped** — and 73 + 24 = 97. Cross-checked against the sweep's own list, which is sorted ascending by id: its first entry is `TRANSCRIPT:0095203e…`, and every `INBOX:` id sorts before every `TRANSCRIPT:` id, so an unmapped INBOX item could not be hiding past the display cap.

**Every non-transcript record ever ingested — 73 of 73 — is mapped. 361 of 385 transcript records (94%) are not.** Nothing else on this channel list contributes a single item to the queue.

That is a sharper claim than "the queue grows", and it moves where the remedy plausibly belongs. The three solutions beneath this node all sit in the sweep — cluster before the queue sees it, corroborate instead of creating, record a read-and-skipped judgement. The split says the sweep is not where the asymmetry originates: every other adapter produces records that distil into needs and leave, and one adapter produces records that never can, because a per-session friction digest is a report about the tool rather than a want anyone has. Whether that argues for fixing this at the transcript adapter — emitting one rolling record per shape instead of one per session — rather than at the queue is a design call for a human, and it is a fourth candidate none of the three existing solutions covers.

**2. A standing claim on this node has cleared, and nothing noticed.** The body above says of `INBOX:2026-07-24-friction-a-backgrounded-session-leaves-no-marker-of-where.md`: "No tool on this surface can repair the mapping — it will reappear every pass until a human sets `source` directly or the merge tool is fixed." It is not on the queue now, and by the sort argument above it cannot be. Whatever repaired it, the prediction no longer holds and the paragraph asserting it does. Not edited out here — a human should decide whether it was fixed or merely re-cited, and the wording is evidence either way.

This is a second instance of the pattern now filed as "A measured bar is only re-taken when a pass feels like it, so a fix reads as working long after it stopped", found on a different node within the same hour as the first. Two is not a rate, but both were found by recounting something a node asserted, which is the only way either would have surfaced.

_Method: two `Glob` counts over the evidence sidecar plus arithmetic against the sweep's own totals; the INBOX conclusion is an inference from the list's sort order, stated so it can be checked. First-party counts over stored records. No node created, no rung moved, nothing mapped — for the reason this node exists._
