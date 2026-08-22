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

## Trend line and a sixth shape — 2026-08-22 (unattended sweep)

Held to one short entry per the 2026-08-17 Issues note. Two facts only.

**Trend: 359 (2026-08-21) → 365.** Up 6 in a day. Still never gone down. Two of the six were captured by this pass's own `ost_ingest_inbox` (`005ca37f…`, `5e29c8b9…`); both were read in full.

**A sixth shape, and like the `sleep` row it survives the "already in the table" test.** `005ca37f…` contains `overwrite src/cli/index.ts? (y/n [n]) not overwritten` — a *shell command* blocking on an interactive prompt with nobody at the keyboard, alongside `(eval):1: === not found` and a `pathspec … did not match any file(s)`. This is not row 3. Row 3 is the agent raising `AskUserQuestion` itself; this is a subprocess the agent invoked stopping to ask, which no amount of discipline about the agent's own question-asking would prevent. The tree holds it — "My unattended run stops at a prompt that assumes a person is sitting there", with "Non-interactive is the default, and any tool that would prompt is made to fail loudly instead" and "Detect that no terminal is attached and answer the prompt from a stated policy" beneath it — so the standing claim ("every record lands in a row the tree already holds") still stands. Route new instances there.

That makes two shapes now found outside the four-row table in two consecutive sweeps (the `sleep`/Monitor row on 2026-08-21, this one today). The table is not wrong, it is under-specified, and the practical consequence is the one already stated for the `sleep` row: **a clustering solution built to the four rows would leave both unclustered.** Worth a builder reading the table as a floor rather than a spec.

**Nothing was mapped, for the reason this node exists.** No tool on this surface records "read and judged redundant."

_Method: full reads of both newly-captured records plus two `Grep` passes over the vault confirming the interactive-prompt shape already has a home. First-party over stored records; no node created, no rung moved._

## Trend, second firing of 2026-08-22 — 365 → 367, no new shape

One short entry per the 2026-08-17 Issues note, and deliberately not a second narrative: the entry above already covers today.

**Trend: 365 → 367.** Both new records were captured by this pass's own `ost_ingest_inbox` and both were read in full. `32113b68…` is three `File has not been read yet` errors — row 1, unmixed. `4badb8cf…` is a denied `Glob` on `/Users/tanner/dev/OST-Agent` plus `No such tool available: Bash` — row 2. No sixth or seventh shape; the six now on record (four in the table, plus the `sleep`/Monitor row and yesterday's interactive-subprocess row) cover both.

**One detail in `4badb8cf…` is worth a builder's eye, because this pass reproduced it exactly.** That session was denied `Glob` on the product repo while `ost_read_repo` answered for the same directory — and this firing hit the identical pair, `Glob` refused and `ost_read_repo` live. That is the separable-grants observation already recorded on "A pass that cannot see the repository cannot set an instrument at all", but it had been an inference from two firings' differing behaviour; here it is one session's mechanically captured transcript and a second firing reproducing it within the day. The consequence for anyone reading a pass's capability claims: "no repo sight" and "no `Glob`" are different statements, and a sweep that checks only the built-in file tools will report itself blind while holding a working read channel.

**Nothing was mapped, for the reason this node exists.** Still no tool call on this surface that records "read and judged redundant."

_Method: full reads of both newly-captured records; the grant asymmetry observed first-hand this pass. First-party over stored records. No node created, no rung moved._

## 2026-08-22 sweep: two new records, both restating held needs, one confirmed first-hand in the same session

`ost_ingest_inbox` captured 2 new transcript records this pass, taking the unmapped backlog from 367 to **369**. Both were read in full via `ost_next_work({evidence})` and neither reveals a need this tree does not already hold. Recorded here rather than as two new Opportunities, which is this node's whole argument.

- **`TRANSCRIPT:cfa8d099-747d-4b5c-8155-05b17e289655`** (4 events: retry ×2, tool_error ×2). Both tool_errors are `File has not been read yet. Read it first before writing to it.` — one on `Edit`, one on `Write`. That is the read-before-write class, already held by the bucket "The file changed after I read it, and the failed edit is how I find out" and already ideated under as "Auto-read a file before the first write or edit to it in a session, instead of erroring".
- **`TRANSCRIPT:c1a38258-17aa-4b18-b4ca-2a2e24870f00`** (3 events: tool_error ×1, retry ×2). The tool_error is `Claude requested permissions to read from /Users/tanner/dev, but you haven't granted it yet.` — a `Glob` denial. Already held: the separable-grants finding on "A pass that cannot see the repository cannot set an instrument at all" records that `ost_read_repo` and the built-in file tools are independent grants over the same directory, observed both ways across firings.

**The second one was reproduced by this pass, in this session, which is worth more than the record itself.** This sweep called `Glob` on `/Users/tanner/dev/OST-Agent` and was denied with that exact message, and then called `ost_read_repo` on the same repository and was served — repo root, `test/`, `src/loop`, `src/ost`, and the full text of `src/eval/coverage.ts`, `src/eval/rollup.ts`, `src/eval/buildable.ts` and `examples/automation/build-pass.sh`. So the two grants are not merely separable in principle across firings; they were observed split **within one session**, with the MCP grant present and the built-in grant absent at the same moment. That removes the remaining reading in which the earlier observation was a scheduling or configuration drift between runs.

**The disposition, and why it is not a skip.** Neither record was mapped to a new node, because mapping either would create a duplicate of a need already on the tree — which is the cost this node exists to name. Neither was discharged from `unmappedEvidence` either, because this pass could not establish from source how a record leaves that list. The tree already carries the tests that would settle it — "Cite three ids from one node and require all three to leave the unmapped list", "A node may cite many sources, so one distillation discharges the whole cluster", and "Scan every node body for the 363 unmapped ids and count both the hits and the negations" — and all three are unrun. **Until one of them has a result, citing ids in a body is a guess about a mechanism, not a use of it**, so this pass declined to write 369 citations on the chance that they discharge. The id-count in that third test's own title (363) against today's 369 is itself a measure of how fast this backlog accrues while the question stays open.

**What a human should take from this.** The backlog is not 369 unmapped needs; it is a growing pile of records that mostly restate a small number of held needs, with no confirmed way to mark one as read. The unblocking move is a result on any one of those three tests, not more mapping.

_Method: `ost_ingest_inbox`, then `ost_next_work({evidence})` on each of the two new ids, read in full. The within-session grant split is first-party observation of this pass's own tool surface. Both records are the agent's own usage — usability evidence, not outside demand. Rung stays at the `assertion` floor._
