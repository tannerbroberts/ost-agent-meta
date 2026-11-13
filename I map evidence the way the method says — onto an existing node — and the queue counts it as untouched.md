---
type: Opportunity
source: 'agent-run:2026-08-22-unattended-sweep'
created: '2026-08-22'
evidence: assertion
authorship: machine
---
#Opportunity #unvalidated #evidence/assertion
[[Count a source citation in a node's prose as a mapping, wherever in the body it appears]]
[[Give a node a structured list of the sources it rests on, and a tool call to add one]]
[[Let a pass explicitly dispose of an evidence record it has read, naming what it corroborated]]

**The need.** The skill's own rule for evidence is "reuse, don't duplicate": when a new record corroborates a need already on the tree, append the corroboration to that node rather than minting a second opportunity saying the same thing. Passes here have followed that rule scrupulously for weeks. The queue does not register any of it. Every correctly-handled record stays in `unmappedEvidence` forever, and the count is now **363** — by a wide margin the largest number in the sweep, and the single biggest reason a pass cannot reach `done`.

## The natural experiment, taken from one sweep's own output

This is not inferred. Today's `ost_next_work` returns `unmappedEvidence` alphabetically from the start of the set, so absence from the head of that list is conclusive rather than an artifact of the 25-item cap. Three records sitting within four characters of each other in that ordering behave differently:

| Evidence id | How the tree records it | In `unmappedEvidence` today? |
|---|---|---|
| `TRANSCRIPT:0b98ae8c-…` | not cited anywhere | **yes** |
| `TRANSCRIPT:0d27cebf-…` | carried as the `source:` of "I probe for files that were never there, because nothing hands me the layout of the workspace I am in" | **no — drained** |
| `TRANSCRIPT:0e0cd6f3-…` | cited in the prose of "The agent has to guess what resources it's actually working with", under a dated Corroboration heading with a full `_Source:_` line | **yes** |

`0d27cebf` sorts between the other two and is simply not in the list; the other two are. The only difference between `0d27cebf` and `0e0cd6f3` is **which part of the file names them** — one is a frontmatter `source:`, the other is prose. `TRANSCRIPT:09ec7cd2-…`, cited by name in two separate nodes' corroboration sections, is also still listed.

So the predicate for "mapped" reads the `source:` field and nothing else. And a node has exactly one `source`. Between those two facts, an evidence record can only ever drain the queue by **causing a brand-new node to be created for it** — which is precisely the act the method tells a pass not to perform when the need already exists.

## Why this is a need and not a preference

The rule and the counter point in opposite directions, and a pass has to disobey one of them:

- Follow the method, corroborate the existing node, and the queue reports the work as never done. Repeat for weeks and you get 363 items that no amount of correct work will ever clear.
- Satisfy the counter, mint a new opportunity per record, and you get 363 near-duplicate nodes — the exact debt `near-duplicate` hygiene, `ost_merge_nodes` and the extent-overlap rules exist to prevent.

The incentive as built rewards the second. That nobody has taken it is a fact about the passes, not about the mechanism.

## Why it belongs under this parent

The parent names the general defect — the queue does not drain when the work is done — and already records four mechanisms of it: shipped solutions still asked for instruments, deferred opportunities still counted under-served, category buckets counted as needing direct solutions, and humans-required tests still listed as owing a command. This is the fifth, it is the same shape (a fact the product holds is applied to some analyses and not others), and it is larger than the other four combined.

**How it differs from its siblings, so it is not one of them wearing a new title:** every sibling concerns a **node** whose settled state the queue ignores. This concerns an **evidence record**, which is a different kind of object, drains through a different predicate, and would be fixed by different code. A repair to any sibling leaves all 363 in place.

## Litmus test — more than one way to address it?

Yes, and the candidates disagree about what a mapping *is*: count a prose citation as one; let a node declare several sources through a structured field; let a pass explicitly dispose of a record it has read and judged; or age records out on time and accept that some real needs go unmapped. Different mechanisms, different failure modes, genuine trade-offs. Passes.

## Limits of this finding, stated so it is not over-read

- **The predicate was not read in source.** It lives in `src/mcp/next-work.ts`, which is 74KB and would truncate on a single read; this pass probed its size and did not read it. The behaviour above is established from the tool's own output, which is strong evidence of *what happens* and no evidence of *how it is implemented*. A builder should confirm the predicate before changing it.
- **363 is the count of records, not of unmet needs.** Most of these are transcript friction records whose shapes this tree already carries; a mechanism that drained them would be recording that they were handled, not surfacing new work. Nobody should read a drained queue as more discovery having happened.
- **Whether an operator wants this queue to drain is unasked.** One could argue every record should stay visible until a human has seen it, and that a growing count is the honest signal. That is the design question and this node does not settle it.

⚠️ Unvalidated. Distilled by an unattended pass from its own tool output; no human has confirmed that a draining evidence queue is what they want. First-party observation of this product's own tooling — it grounds feasibility and usability, not demand. No command executed, no result recorded; rung at the `assertion` floor.

## Standing measurement — what eight firings of sampling established (consolidated 2026-11-10)

**For a firing that meets a four-digit `unmappedEvidence` count: the head of the queue has been read many times and does not need reading again.** The records `00032886`, `0018a4eb`, `004a28b8`, `00691b0d`, `0095203e`, `00b567f9`, `01960990`, `030e5db3` and `08e10880` have each been read in full by several firings, and every one repeats a need the tree already holds. Read a record only if it is the one this firing's own ingest captured, or if it comes from somewhere not listed below. Add a line here only when a record holds a need the tree lacks, or when the growth rate changes.

**The count.** 363 (2026-08-22), 1017 (10-13), 1107 (10-18), 1600 (11-09), 1625 (11-10). That is about 21 a day since mid-October, and roughly one per firing: each ingest captures the previous firing's own session.

**How the queue has been sampled, and what each sample found.**

| Sampled by | Records | New needs found |
|---|---|---|
| Head of the alphabetical order (10-13, 11-10) | 5, then 8 | 0 |
| Tail (10-16) | 7 | 0 |
| Middle (10-17) | 5 | 0 |
| Error signature, one Grep over every evidence file for refusals from ten of this product's tools (11-10) | 49 lines, 6 signatures | 0 (5 of 6 named literally in a node, the sixth held in paraphrase) |
| The record each firing's own ingest captured (10-13 to 11-10) | about 8 | 0 |

The same ids recur across rows, so these do not add up to a count of distinct records. None of it is a random sample and none of it gives a rate.

**The shapes that keep recurring, each already on the tree.** Permission denials on withheld tools and on the product-repo path. A brace in a Grep glob read as an alternation group. Write or Edit refused on a file not yet read. A Monitor command refused for command substitution. `ost_read_repo` on a path that does not exist (`src/instruments` guessed in 11 sessions, `src/evidence` in 6) or with no product repo configured (7 sessions). `ost_set_instrument` refusing `-t "<name>"` as shell punctuation, which is the form the loop prompt's own "strong instrument" example uses. `ost_read_tree` on a title not on the tree. Refusals from `ost_edit_node`, `ost_set_evidence` and `ost_create_node` for an omitted section, a rung above the ceiling, a bar-less threshold. The prescribed `ost_ingest_inbox` / `ost_next_work` re-call filed as `retry`.

**Three structural facts the sampling turned up.**
- **Prose citations do not drain.** On 2026-10-18, 12 of the 25 head-of-queue ids were cited by name in at least one node's prose and were still listed. `0095203e` was cited in seven nodes.
- **Reading the queue feeds it.** Each firing reads the head with `ost_next_work({evidence})` and re-reads the same few node bodies. The harvester files those reads as `retry` events, and that session becomes the next firing's new record. The record captured on 2026-11-10, `6bb858d1`, is 12 such events, including reads of this node.
- **No human-carried evidence is waiting.** On 2026-11-09 all 51 `INBOX_*` evidence ids were found as the `source:` of at least one node, and the listing opens at `TRANSCRIPT:0003…`, ahead of which any unmapped `INBOX:` id would sort. The queue is this vault's own session transcripts. The newest `INBOX_*` file is dated 2026-08-20; nothing operator-written or from outside has arrived since.

**What no firing did, on purpose.** No node was minted per record, and no further corroboration lines were appended to nodes that already carry several. The three candidates under this node are where the count gets fixed, and choosing one is the operator's.

**Limits.** `USAGE_*` records were never checked one by one. "Already on the tree" means a literal or paraphrase match in a node body, judged by the pass that read it. The error-signature Grep covered this product's tools and no harness tool. Everything here is this agent's own surface observed by itself: it grounds usability, not desirability. Nothing was executed and no rung, lane, instrument or status changed. `ost_check` is withheld on the unattended surface, so none of these writes was verified by the invariant checker.

## History
- 2026-11-10 body edited, dropping `## 2026-10-13 — the count this node opens on is now 1017, nearly triple`, `## 2026-10-16 — the tail of the queue looks like its head`, `## 2026-10-17 — the middle of the queue looks like both ends`, `## 2026-10-18 — 12 of the 25 records at the head of the queue are already cited in node prose`, `## 2026-11-09 — 1600 now, and the queue grows faster than any firing reads it`, `## 2026-11-09 (later firing) — the queue by channel: every human-carried record is mapped, and the last one arrived on 2026-08-20`, `## 2026-11-10 — sampled by error signature across the whole folder, not by position: still nothing new` — Seven dated measurement sections (2026-10-13 to 2026-11-10) had grown this node to 20KB, each firing re-reading the same head-of-queue records and appending the same verdict. Folded them into one standing measurement that tells a firing what is already settled before it spends reads. The need statement and its five original sections are reproduced verbatim; every distinct count is kept; git holds the prior text.

## 2026-11-11 — the growth rate changed, and one usage record says what a day of firings spends

Added under this node's own rule (a line only when the growth rate changes or a record holds something new).

**The count.** 1658 at this firing, up from 1625 on 2026-11-10. That is 33 in about a day against the roughly 21 a day recorded above.

**Why, read from a record no firing had opened before.** `USAGE:2026-11-11` is the first `USAGE_*` record read in full from this surface (the Limits above say none had been). It is a machine rollup, no narrator: 23 sessions, 311 tool calls, 0 failed. By tool: `ost_next_work` 158, `ost_read_tree` 99, `ost_read_repo` 30, `ost_ingest_inbox` 23, `ost_append_to_node` 1. So 310 of 311 calls were reads, and 23 firings produced one write between them. Each of those sessions is also one new transcript record, which is the rate above.

**What that adds.** The loop's stop condition said `go` for this firing on three counts: unmapped evidence, one under-served opportunity, and 70 solutions missing instruments. Each is recorded on its own node as not clearable from the unattended surface (this node; the standing hold on "The agent can decompose my goal but cannot acquire and test its own guesses about how to reach it"; the standing finding on "Route the humans-required solution into the ask queue instead of dropping it from the instrument queue", whose cheap check read 23,611 bytes again today). So the loop is firing about 23 times a day on counters that no firing can move, and the firings' own reads are most of what the queue then grows by.

**This firing.** Its ingest captured `TRANSCRIPT:8def40d1-1dc3-4d89-89d8-a919f0972cd7`: 12 events, all filed `retry`, all reads of node bodies and head-of-queue records. No need the tree lacks. No node was minted for it or for the usage record.

**Limits.** One usage record, one day. 23 sessions is the trace's count of sessions that called this server, not a count of loop firings read from the scheduler. "Cannot move" rests on the three nodes' recorded findings, re-checked today only by the byte probe and by reading the hold. Nothing was executed, and no instrument, lane, rung or status changed. Unverified by design (`ost_check` is withheld on this surface).

## 2026-11-12 — the growth rate fell back, and the standing "do not re-read the head" rule did not reach this firing in time

Added under this node's own rule (a line only when the growth rate changes).

**The count.** 1667 after this firing's ingest, against 1658 recorded on 2026-11-11. That is 9 in about a day, down from 33 the day before and below the roughly 21 a day of October. The cause was not read: no `USAGE_*` record was opened this firing, so whether the loop fired less often or sessions were simply not harvested is unknown.

**This firing's captured record.** `TRANSCRIPT:d850eff5-2428-4355-a5e0-a17fde52d44f`: 35 events (33 `retry`, 2 `tool_error`), the largest single record noted on this node. Both errors are the brace-in-a-Grep-glob refusal (`'{A': unclosed alternate group`) already held by "A string I meant literally is read as syntax, so the command fails instead of searching". The retries are reads of head-of-queue records and of the same few node bodies. No need the tree lacks; no node minted.

**One observation about this node's own instruction.** The standing measurement above says the head of the queue need not be read again. This firing read four head records (`00032886`, `004a28b8`, `0316ae5c`, `030e5db3`) in full before it opened this node, because nothing in the sweep response points here first. The instruction is correct and is stored one read too late to save the reads it is about. That is the same gap recorded on 2026-11-01 under "Maintain a running per-item task list the next pass reads before reconstructing state itself".

**Limits.** One day's difference between two counts taken at unrecorded times of day. Nothing was executed, and no instrument, lane, rung or status changed. Unverified by design (`ost_check` is withheld on this surface).

## 2026-11-13 — the rate is back near 29 a day, so the 9 on 2026-11-12 was the odd day

Added under this node's own rule (a line only when the growth rate changes).

**The count.** 1696 after this firing's ingest, against 1667 on 2026-11-12. That is 29 in about a day. The series now reads 33, 9, 29 a day, so the dip was one day and the queue is growing at roughly the 2026-11-11 rate again. The cause was not read; no `USAGE_*` record was opened.

**This firing's captured record.** `TRANSCRIPT:292db0a5-177c-47bb-95c8-93363bafd61e`: 12 events, all `retry`, all reads of head-of-queue records and of this node, the standing hold, and the instrument-bucket finding. No need the tree lacks; no node minted.

**The "one read too late" gap from 2026-11-12 repeated.** This firing read four head records (`02326b78`, `00032886`, `030e5db3`, `004a28b8`) before it opened this node. All four repeat needs already held.

**Limits.** Two counts taken at unrecorded times of day. Nothing was executed, and no instrument, lane, rung or status changed. Unverified by design (`ost_check` is withheld on this surface).
