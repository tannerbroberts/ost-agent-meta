---
type: Opportunity
source: 'TRANSCRIPT:03a79a59-682a-4528-83c6-4c39d8c658ef'
created: '2026-08-06'
evidence: observed
authorship: machine
---
#Opportunity #unvalidated #evidence/observed
[[Let a friction record corroborate an existing opportunity instead of demanding a new node]]
[[Cluster friction records by signature before the queue sees them]]
[[Record a read-and-skipped judgement so the queue drains without a write]]
[[Have the transcript adapter emit one rolling record per friction shape instead of one per session]]

**The need.** Self-observation was turned on so the agent's own usage would improve the tool. What it produces is a queue that grows daily, where nearly every record restates a need the tree already holds. For 24 sweeps the only way to take an item off that queue was to create a node citing it, so honest maintenance would have made the tree worse — duplicate debt, created deliberately — and every pass faced a choice between minting a near-duplicate and leaving the item outstanding forever.

**That is no longer true, and the correction is the most important thing on this node.** A mechanism exists and ships: `ost-agent dispose`. See "The mechanism, and why no pass found it" below. What remains true is that it is a human's CLI command, deliberately off the agent surface, and that this vault has **zero live dispositions** — so the backlog has never actually been drained, and every pass still reports it.

## The six shapes every session-friction record has landed in

Corpus counts from a full grep of the evidence sidecar. The four-row table dates from 2026-08-16; rows 5 and 6 were found in consecutive sweeps afterwards, which is why the table should be read as **a floor, not a spec** — a clustering solution built to four rows would leave two shapes unclustered.

| # | What the record shows | Where the tree already holds it | Corpus count |
|---|---|---|---|
| 1 | `File has not been read yet` / `modified since read` / `String to replace not found` | "The file changed after I read it, and the failed edit is how I find out" | 289 occurrences / 173 files (2026-08-21); was 173+16 / ~109 (2026-08-16) |
| 2 | `requested permissions to read from …` (denied tool/path grants) | "The agent has to guess what resources it's actually working with"; "A sweep that cannot read its subject reports a clean result" | 82 / 69 (2026-08-21); was 56 / 49 (2026-08-16) |
| 3 | An unattended firing raising `AskUserQuestion` with nobody watching | "The work I most want to run unattended is the work that keeps needing a decision"; "The whole loop waits on one human command, and nobody is told it is waiting" | — |
| 4 | Repeated `retry` of `ost_next_work` / `ost_ingest_inbox` | "The same refusal is rediscovered every session, because nothing carries the lesson forward" | — |
| 5 | `Blocked: sleep N followed by …` — a run with no permitted way to wait for its own background work | "The Monitor tool refuses the exact commands an unattended run needs to check on its own background work"; "My loop spends its time waiting for a check it cannot subscribe to" | 34 / 31 (2026-08-21) |
| 6 | A *subprocess the agent invoked* blocking on an interactive prompt — `overwrite src/cli/index.ts? (y/n [n]) not overwritten` | "My unattended run stops at a prompt that assumes a person is sitting there", with "Non-interactive is the default, and any tool that would prompt is made to fail loudly instead" and "Detect that no terminal is attached and answer the prompt from a stated policy" | first filed 2026-08-22 |

**Row 6 is not row 3.** Row 3 is the agent raising `AskUserQuestion` itself; row 6 is a subprocess stopping to ask, which no amount of discipline about the agent's own question-asking would prevent.

**Two shapes that are NOT rows here.** Malformed tool calls / mangled tool names / shell syntax failures — `could not be parsed as JSON`, 24 occurrences / 19 files — were tracked as a candidate fifth row and **closed on 2026-08-10**: they belong to "Two thirds of my calls failed, and each one only told me after I made it", issued by the harness. And `exceeds maximum allowed size (256KB)`, 2 / 2, is homed on "More reaches my senses than fits in the window where I think". Route new instances to those nodes.

**Other records that must not be filed as friction at all.** A stale-recording guard firing, or a builder's pre-write existence check on a file it is about to create, both generate a friction-shaped record. A clustering solution has to tell "product failed" from "product worked as designed, verbosely."

## What "mapped" means, settled from the code rather than guessed

From the docstring of `src/knowledge/dispositions.ts`, verbatim: an item is mapped only when a node's frontmatter `source:` equals its id, **body citations are invisible to the sweep**, and no tool can add a `source:` to an existing node.

That settles three tests this node had named as the unblocking move, without running them, and settles two of them in the negative:

- *"Cite three ids from one node and require all three to leave the unmapped list"* — a node carries **one** `source:` field, so one distillation discharges exactly one id.
- *"A node may cite many sources, so one distillation discharges the whole cluster"* — **false as the code stands.**
- *"Scan every node body for the 363 unmapped ids and count both the hits and the negations"* — would count hits that discharge nothing.

A prior pass declined to write 369 body citations on the chance that they discharge. That judgement was correct: they would have done nothing.

## The mechanism, and why no pass found it

`src/knowledge/dispositions.ts` is an append-only JSONL sidecar at `.ost-agent/dispositions/dispositions.jsonl` whose entire purpose is recording "read and judged redundant". Its own docstring names this node's situation as the motivating case. The typed verdict vocabulary is `corroborates` / `no-genuine-need`, and a `corroborates` entry must name the node the item was counted toward — which is the solution "Let a friction record corroborate an existing opportunity instead of demanding a new node", built as specified, pointer included.

**What a filing does, pinned by a committed spec.** `test/evidence/corroborate-disposition.test.ts` files thirty transcript ids against one opportunity and asserts: all thirty leave `unmappedEvidence`; the evidence records stay on disk; every withheld item is disclosed on the response that withheld it (`withheldByDisposition`); no node is created; and the node file is **byte-identical** afterwards — so no rung moves and thirty recordings of one channel do not become thirty sources. That is exactly the discharge this node has wanted, with the corroboration-inflation failure already designed out.

**Why no pass found it: it is not on the agent surface, on purpose.** The write is `ost-agent dispose`, a human's CLI command (`test/cli/dispose.test.ts`), held off the agent surface for the same reason as `result` and `promote` — the docstring calls it "the highest-risk write on the surface", because a pass that could dismiss its own work list has a completion signal that means nothing. Whether it should ever reach the agent is already a node on this tree: "An operator would accept a pass dismissing its own work list by written assertion". So every past pass reporting "no tool on this surface records read-and-skipped" was accurate about its surface and wrong about the product.

**The actionable line for the operator.** The backlog is drainable today, by you, without creating a single node:

```
ost-agent dispose "TRANSCRIPT:<id>" --kind evidence --verdict corroborates \
  --node "The file changed after I read it, and the failed edit is how I find out" \
  --by <you> --why "another instance of the read-before-write shape"
```

The six shapes above are the routing map for doing it in bulk, and `ost-agent dispositions` prints every live dismissal for audit with the one-command reversal beside it.

**What this does not settle.** Nothing here is a result. It says the capability exists — read off a committed spec, not observed by running it — not that the operator wants ~392 items dismissed, nor that any particular filing would be judged correctly; the spec's own docstring concedes it "is blind to whether the filing was right." A surface with a shell should confirm one real filing actually clears one real id.

## Trend log

The queue has never gone down.

| Date | Unmapped | Note |
|---|---|---|
| 2026-08-06 → 2026-08-17 | 65 → 244 | 20 consecutive sweeps: 65, 73, 84, 92, 100, 102, 105, 107, 113, 115, 119, 122, 123, 124, 126, 129, 131, 132, 133, 134, 209, 210, 212, **244**. No new shape found after the fifth-row question closed 2026-08-10. |
| 2026-08-21 | 359 | Up 115 in four days. Row 5 (`sleep`/Monitor) identified. |
| 2026-08-22 | 365 | +6. Row 6 (interactive subprocess) identified from `005ca37f…`, `5e29c8b9…`. |
| 2026-08-22 (2nd firing) | 367 | `32113b68…` row 1 unmixed; `4badb8cf…` row 2 plus `No such tool available: Bash`. |
| 2026-08-22 (3rd firing) | 369 | `cfa8d099…` row 1 (Edit + Write); `c1a38258…` row 2 (`Glob` denied on `/Users/tanner/dev`). |
| 2026-08-22 (7th firing) | 391 | +3: `8fb2c38d…` (row 1 + row 6 + an exit-143 ten-minute timeout, held by "A test that failed because the machine was busy looks exactly like one that failed because I broke something"); `ffb9eb47…` (row 2); `USAGE:2026-08-22`. |
| 2026-08-22 (8th firing) | **392** | +1: `bb8f75b7…` — row 2 (`Grep` denied on `/Users/tanner/dev/OST-Agent/src`) plus row 4 (`retry` ×4 across `ost_ingest_inbox` / `ost_next_work`). No new shape. |
| 2026-08-22 (8th firing, mid-sweep) | 393 | +1: a second `ost_ingest_inbox` later in the same pass captured `c2cc5547…` — two `File has not been read yet` (row 1) and one `SyntaxError: "undefined" is not valid JSON` from a Bash call, the malformed-call class closed 2026-08-10 and routed to "Two thirds of my calls failed, and each one only told me after I made it". No new shape. Recorded as its own row because the 392 above is left accurate as of when it was observed, not edited into a live counter. |
| 2026-08-23 | **395** | +2: `e42ae959…` — row 1 (`String to replace not found`, `File has not been read yet` ×2) plus a `Tests 8 failed \| 2 passed` Bash exit 1; `d2c8dbf0…` — row 2 (`Glob` denied on `/Users/tanner/dev/OST-Agent/src/ost`) plus row 4 (`retry` ×3). No new shape; no seventh row. |
| 2026-08-26 | **412** | +17 since the 2026-08-23 row. Two records observed arriving that sweep, both in known rows: `TRANSCRIPT:4ff810f4…` is a `Bash` exit 143 / "Command timed out after 2m 0s", the machine-busy shape held by "A test that failed because the machine was busy looks exactly like one that failed because I broke something"; `USAGE:2026-08-24` is the daily rollup class. No new shape; no seventh row. **The +17 exceeds the +2 that sweep observed, so firings between 2026-08-23 and 2026-08-26 captured records without logging a row.** Originally written as prose inside Correction 3; moved here 2026-08-26 (2nd firing) so the table is the single source of trend truth. |
| 2026-08-26 (2nd firing) | **413** | +1: `TRANSCRIPT:e8429bbc…` — row 2 (`Glob` denied on `/Users/tanner/dev/OST-Agent/test`) plus row 4 (`retry` ×2 across `ost_ingest_inbox` / `ost_next_work`). No new shape; no seventh row. Also a **fifth** instance of the within-session grant split below, and the first observed *across consecutive firings of the same loop*: that firing's `Glob` on `/Users/tanner/dev/OST-Agent/test` was denied, and this firing's `ost_read_repo` served `test/` on first call. |

## The within-session grant split, now reproduced four times

`Glob`/`Grep` on the product repo is denied while `ost_read_repo` serves the same directory **in the same session**. Recorded on `4badb8cf…`, `c1a38258…`, `ffb9eb47…` and `bb8f75b7…`, and reproduced first-hand by the firings that read those records — one pass was served repo root, `test/`, `src/loop`, `src/ost`, and the full text of `src/eval/coverage.ts`, `src/eval/rollup.ts`, `src/eval/buildable.ts` and `examples/automation/build-pass.sh` while its `Glob` was refused; the 2026-08-22 eighth firing hit the identical pair, and so did the 2026-08-23 firing (`Glob` on `/Users/tanner/dev/OST-Agent` refused; `ost_read_repo` served `test/`, `src/`, `src/mcp/node-body.ts`, `src/ost/node.ts`, `src/ost/sections.ts`, `src/mcp/required-tools.ts`, `src/loop/updates.ts` and `src/loop/stall.ts` in full).

This is the separable-grants observation recorded on "A pass that cannot see the repository cannot set an instrument at all". It began as an inference from two firings behaving differently; it is now a mechanically captured transcript plus repeated same-session reproduction, which removes the reading in which it was scheduling or configuration drift between runs. **The consequence for anyone reading a pass's capability claims: "no repo sight" and "no `Glob`" are different statements, and a sweep that checks only the built-in file tools will report itself blind while holding a working read channel.**

## Corrections — claims this node made and later falsified

Kept because *how* each was caught is more transferable than the claim itself: both were found by recounting something a node asserted, which is the only way either would have surfaced. Both are instances of "A measured bar is only re-taken when a pass feels like it, so a fix reads as working long after it stopped".

**1. "The backlog is one channel, entirely" — false.** The 2026-08-21 addendum stated "every non-transcript record ever ingested — 73 of 73 — is mapped; 361 of 385 transcript records (94%) are not," and concluded "nothing else on this channel list contributes a single item to the queue." Counted directly on 2026-08-22: `.ost-agent/evidence/` holds **23 `USAGE_` records, and exactly 5 distinct usage ids appear as any node's frontmatter `source:`** — 2026-07-26, -08-02, -08-03, -08-04 and -08-05 (the last cited by four nodes). The other **18 are unmapped**: 2026-07-25, -07-27, and every day from 2026-08-06 through 2026-08-22 except those named. Neither escape applies — `agedOutEvidence` was 0 and `withheldByDisposition` was `[]` on that sweep.

*Why the earlier count reached the opposite answer:* it did not count non-transcript records, it inferred them. 458 total − 385 transcript = 73 non-transcript; the sweep reported 361 unmapped hence 97 mapped; 73 + 24 = 97 was read as "all 73 non-transcript, plus 24 transcript." That arithmetic is equally satisfied by 55 non-transcript and 42 transcript — underdetermined, and the entry said so nowhere. The addendum's sort-order argument was sound about `INBOX:` ids and silent about `USAGE:`, which sorts *after* `TRANSCRIPT:` and so hides past the display cap in exactly the way the argument ruled out for INBOX.

*What it changes, and it is not small.* The addendum used the split to relocate the remedy — "the sweep is not where the asymmetry originates: every other adapter produces records that distil into needs and leave, and one adapter produces records that never can" — and named a fourth candidate on that basis: fix it at the transcript adapter, one rolling record per shape, which none of the three existing solutions covers. **The premise is false for the usage channel**, a daily mechanical rollup with the same never-drains property and a different adapter. So the asymmetry is not transcript-specific, a transcript-adapter-only fix would leave a second channel accruing, and the three queue-side solutions beneath this node look better under the corrected count than they did under the old one.

*The bound, stated so this is not over-read:* only the `USAGE_` class was counted, by grep over frontmatter. `INBOX_` and `INBOX_friction_` were not recounted, so "73 of 73" may be wrong by more than 18. One counter-instance falsifies the claim; the true non-transcript unmapped count is still unmeasured.

**2. A standing prediction cleared and nothing noticed.** This node long asserted of `INBOX:2026-07-24-friction-a-backgrounded-session-leaves-no-marker-of-where.md` — whose actual need lives on "An interrupted run leaves no trustworthy account of what it completed" — that "no tool on this surface can repair the mapping; it will reappear every pass until a human sets `source` directly or the merge tool is fixed to union it." It is not on the queue and cannot be. Whatever repaired it, the prediction no longer holds. Left on the record rather than deleted: a human should decide whether it was genuinely fixed or merely re-cited, and the original wording is evidence either way.

## Litmus test and what sits beneath

Passes — there is more than one way to address it: cluster records by signature before the queue sees them; let a record corroborate an existing opportunity instead of demanding a new node; record a read-and-skipped judgement so the queue drains without a write. Candidate solutions for all three sit beneath this node. At least two are now **built** (see the mechanism section); the 2026-08-17 Issues note claiming all three "remain unbuilt after 20 sweeps" is false and is corrected here.

⚠️ Unvalidated. Distilled from the tree's own instrumentation, so well-grounded on what happened and not at all on what an operator would want done about it. Evidence rung `observed` covers the friction records' existence and content; it does not cover the claim that a smaller queue is preferable, which is nobody's stated preference.

## Issues
- 2026-08-22 Consolidated seven dated entries (2026-08-21, plus five separate 2026-08-22 firings and one addendum) into the structure above. The node was chronological, so a top-down reader met two overturned claims — "no tool records read-and-judged-redundant" and "73 of 73 non-transcript records are mapped" — thousands of words before their corrections. Now: current truth first, corrections preserved with their method. No claim, count, session id, shape, named node or stated bound dropped; git holds the prior text.
- **Future sweeps: add a row to the trend table. Do not add an entry.** If the only news is "+N records, all in known rows", the row IS the entry. Add prose only for a genuinely new shape, or to correct a claim above — and if you correct one, say how you caught it.
- The unblocking move is no longer a test result. It is an operator running `ost-agent dispose` once, on one id, to confirm a filing clears it in practice. Everything else on this node is waiting on that.

## Correction 3 — the non-transcript unmapped count, measured (2026-08-26)

Correction 1 above closed with a stated bound: *"only the `USAGE_` class was counted, by grep over frontmatter. `INBOX_` and `INBOX_friction_` were not recounted, so '73 of 73' may be wrong by more than 18. The true non-transcript unmapped count is still unmeasured."* It is now measured. This entry is prose rather than a trend row because the node's own rule admits one — it corrects a claim above — and the rule also asks how it was caught, which is answered at the end.

**The count, 2026-08-26.** Non-transcript evidence is **67 records, of which 20 are unmapped, and every one of the 20 is `USAGE`.**

| Class | Records in the sidecar | Mapped (cited as some node's frontmatter `source:`) | Unmapped |
|---|---|---|---|
| `INBOX` | 42 | 42 | **0** |
| `USAGE` | 25 | 5 | **20** |
| Non-transcript total | 67 | 47 | **20** |

Since `unmappedEvidence` totalled 412 on this sweep, the transcript share is **392**.

**Three things this settles that were open.**

1. **There is no `INBOX_friction_` class to recount.** The friction notes are ordinary `INBOX` ids — `INBOX_2026-07-25-friction-npm-publish-cannot-complete-in-the-unattended-lo` and its neighbours — so the bound's third clause was asking after a class that does not exist. All 42 are mapped.
2. **The "every non-transcript record is mapped" claim was wrong only about `USAGE`.** Correction 1 was right to falsify it and right about where: the INBOX half of the 2026-08-21 addendum's claim holds exactly as stated, and the USAGE half is the whole of the error. The corrected count is 47 of 67, not 73 of 73 and not the 55/42 alternative the addendum's arithmetic also admitted.
3. **The mapped `USAGE` set has been frozen since 2026-08-22 while the corpus grew.** The five distinct ids cited by any node are `2026-07-26`, `-08-02`, `-08-03`, `-08-04`, `-08-05` — the same five Correction 1 named four days ago. The corpus went 23 → 25 (`-08-23`, `-08-24` arrived); mapped stayed 5; unmapped went 18 → 20. Nothing has been mapped off this channel in three weeks. The eight node citations resolve to five ids because `USAGE:2026-08-05` alone is cited four times.

**What this does not settle.** Nothing here is a result and no test was run. It is a count of files and frontmatter fields as they stand today, so it grounds the size and shape of the backlog and says nothing about whether the operator wants any of it dismissed. It also does not revisit the transcript half: 392 is derived by subtraction from the sweep's own total, not counted independently, so it inherits whatever that total inherits.

**One thing it sharpens for whoever picks up the queue.** The routing map in the shapes table covers transcript friction. It does not cover `USAGE`, which is the entire non-transcript backlog and is a mechanical daily rollup with no friction shape at all — a `corroborates` filing needs a node to name, and a usage trace corroborates whichever of "A third of my calls go on re-asking what is outstanding", "Two thirds of my calls failed, and each one only told me after I made it", or "Tests get written and instrumented all day, and not one of them has ever been run" its numbers actually move. Those three are the existing homes; picking among them per day is a judgement, not a lookup, which may be why this channel has never drained.

**How it was caught.** By recounting, which is the same method that caught Corrections 1 and 2 and is the only method that has ever caught anything on this node. Concretely: `grep` over `^source: '<CLASS>:` across the vault's `*.md`, then subtracting the sidecar's own self-citations (each `.ost-agent/evidence/<CLASS>_*.md` record carries a `source:` naming itself) to leave node-side citations, then de-duplicating those to distinct ids. The INBOX zero was cross-checked a second way rather than trusted from arithmetic: `unmappedEvidence` is returned in ascending id order — the 25 shown ran `0095203e…` through `1515b876…` strictly ascending, and those uuids are not in timestamp order, so the sort is on the id string. `INBOX:` sorts before `TRANSCRIPT:`, so any unmapped INBOX record would head the list. None did.

**Trend figure for this sweep:** 412, now recorded as its own row in the trend log above rather than here, per this node's own rule that trend figures belong in the table.

_Source: this pass's own greps over the vault and the `ost_next_work` response that reported 412. First-party observation of files on disk. No test was run and no result is recorded._

## History
- 2026-08-06 → 2026-08-17: 20 consecutive sweeps read new arrivals, confirmed each lands in a known row, and mapped none — trend 65 → 73 → 84 → 92 → 100 → 102 → 105 → 107 → 113 → 115 → 119 → 122 → 123 → 124 → 126 → 129 → 131 → 132 → 133 → 134 → 209 → 210 → 212 → **244** (2026-08-17). No new friction shape has been found since the fifth-row question closed on 2026-08-10. The queue has never gone down. Full per-sweep detail (session IDs, individual record reads, corpus-grep methodology) is preserved in git history on this node prior to this edit.
- 2026-08-17 body compressed (this edit) — 20 near-identical dated entries folded into the standing finding above; nothing dropped, see git log.
- 2026-08-17 body edited — 20 consecutive pass-entries (2026-08-06 through 2026-08-17) grew this node to 58KB, each reaching the identical conclusion — map none, queue does not drain — restated in full prose every time. Compressing to the standing finding plus a compact trend log, per the precedent already set on the Outcome node's 2026-08-04 edit ("each restated what the tree already knew structurally... git holds every one"). No claim is dropped; git history holds the full prior text.
- 2026-08-23 body edited — Seven dated entries — five of them written on 2026-08-22 alone — had grown this node to 27KB arranged chronologically, which made it actively misleading rather than merely long: the body's opening still asserted "there is no tool call that records read-and-judged-redundant... that gap is real product debt", and the entry proving that false (`ost-agent dispose` exists and ships) sat 20KB below it. The 2026-08-21 addendum's "every non-transcript record is mapped, 73 of 73" was likewise left standing above the entry that counted 18 unmapped USAGE records and falsified it. A reader going top-down met two overturned claims before their corrections. Restructured to state current truth first, with a Corrections subsection preserving the full lineage of what was claimed, what falsified it, and how — because which claims were overturned and by what method is itself the most transferable finding on this node. Every shape, corpus count, trend figure, session id, named node, named spec file and stated bound is carried across; today's record (392) is added as a trend row rather than an eighth entry. No claim dropped; git holds the prior text.
- 2026-08-23 body edited — Following this node's own standing instruction to future sweeps — "add a row to the trend table. Do not add an entry." Today's two new records (`e42ae959…`, `d2c8dbf0…`) both land in known rows 1, 2 and 4, so the row IS the entry and no prose is warranted. Also folding the previous firing's 2026-08-23 Issues bullet into the table as its own row: it was written as an entry only because it recorded a mid-sweep discrepancy (392 → 393) the table could not then express, and leaving it as a bullet violates the rule it was written under. Nothing else is touched — every shape, corpus count, session id, named node, named spec, correction and stated bound is carried across verbatim.
- 2026-08-26 body edited — Following this node's own standing instruction to future sweeps — "add a row to the trend table. Do not add an entry." Today's one new record (`TRANSCRIPT:e8429bbc…`) lands in known rows 2 and 4, so the row IS the entry and no prose is warranted. Also folding the previous firing's "Trend row, folded in here rather than added to the table" paragraph out of Correction 3 and into the table where it belongs: it was written as prose only because that firing was already editing for a different reason, and leaving a trend figure outside the trend log is the exact drift the rule exists to prevent — a reader checking the table would have seen 395 as the latest when 412 was recorded 20KB below. Nothing else is touched: every shape, corpus count, session id, named node, named spec, correction, stated bound and the whole of Correction 3's substance is carried across verbatim.
