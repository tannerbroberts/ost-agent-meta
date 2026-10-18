---
type: Opportunity
source: 'TRANSCRIPT:8275c757-fcf0-46d1-9d35-bfab1fdd33f9'
created: '2026-10-17'
evidence: observed
authorship: machine
---
#Opportunity #unvalidated #evidence/observed
[[Scan only the entries that are conversation turns, so the host's request copies never reach the retry check]]
[[Mark each retry with whether its call id was new, and leave the decision to discount it with the reader]]
[[Take the host's tool_use id as the identity of a call, and build no notion of a repeated call here]]

**The need (operator's voice):** "When a session record says the agent retried a call eight times, I read that as eight times it hit something and had to try again. If it actually made each of those calls once, the record is telling me the agent struggled where it did not, and I will go looking for a problem that is not there."

## What was observed, first-party, on 2026-10-17

`TRANSCRIPT:8275c757-fcf0-46d1-9d35-bfab1fdd33f9` (an unattended firing earlier the same day) was filed as **8 friction events, retry ×8, and nothing else**: one `ost_read_repo`, four `ost_read_tree`, and three `ost_next_work` with an `evidence` argument.

I grepped the raw session file for each event's `tool_use` id. **Every one of the 8 ids appears on exactly two lines.** The first copy is in the ordinary assistant entry. The second copy is in an entry the host writes with `"type":"api-request-blob"`, which has no `parentUuid` or `isSidechain` and is not a conversation turn. For example, `toolu_01YPhDz2pr6v1PYvgNMzf4pr` is on line 56 (assistant) and line 60 (api-request-blob), and the blob on line 77 holds all three `ost_read_tree` ids from lines 68, 70 and 72. These are not repeated calls. The agent made zero genuine retries in that session.

**When the second copy appears.** In this session, all 3 turns that made parallel tool calls were copied into a following api-request-blob. Neither of the 2 turns that made a single call (lines 38 and 100) was copied. So far the copying only follows parallel batches, but that is 5 turns in one file, not a rule.

The same pattern is in `TRANSCRIPT:a6cedf56-1e19-4ed7-93da-043fa036ab1b`: two parallel pairs, each id on two lines (52/60, 54/60, 66/73, 68/73). A third session, `TRANSCRIPT:015d5a7e-66f4-4c02-b7c1-bb9c91267f3c`, has no duplicated ids at all. Its two retries are the genuine prescribed repeats the parent node describes. So the two causes are independent and can appear separately.

## The mechanism, read from the code

`extractFriction` in `src/adapters/transcript.ts` has two gaps, and they stack:
- **It reads every entry's `message.content`, whatever the entry's `type`.** It never checks for `assistant` or `user`, so the host's bookkeeping entries are scanned as though they were turns.
- **It decides a retry with `` const signature = `${name}:${input}` `` and never consults the block's `id`.** So once a block is scanned twice it cannot tell a call made twice apart from one call written twice.

The existing spec hides both. The fixture helper `line()` in `test/adapters/transcript.test.ts` writes only turn-shaped entries, and `assistantTool` gives every call the same id, `"t1"`. So the one retry test ("reports a repeated identical tool call as a retry") cannot tell the cases apart either. A builder keying on the id would also have to give that fixture distinct ids, or the existing test would start failing for the wrong reason.

## Why this is not the parent, and not its sibling causes

The parent node is about **prescribed** repeats: the loop really calls `ost_next_work` twice, with two different ids, because its procedure says to. This node is about calls that happened **once**. Torres's test, both ways:
- Skipping non-turn entries, or keying the retry check on the `tool_use` id, removes every event here and none of the parent's. Prescribed repeats are two real turns with two ids, so they still file.
- "A human-edited manifest of loop-prescribed call sequences the harvester suppresses" removes the parent's events and none of these. The calls here take arguments and are not loop-prescribed, so no manifest would name them.

Two of the parent's three solutions, "Drop the retry class entirely and count only events carrying a refusal or an error" and "Take the host's own error flag as the definition of friction instead of authoring one here", would remove both causes, by giving up retry detection entirely. That overlap is real and a human comparing them should weigh it. A narrower fix only exists for this cause.

## Litmus (more than one way to address this?)

Yes: scan only the entry types that are turns; key the retry check on the block id; stop inferring retries at all; or keep the inference but label each retry with whether its id was new, so a reader can discount it. Passes.

## Why it costs something

The parent's 2026-10-11 census counts 775 evidence records containing any retry and attributes the class mostly to prescribed repeats. Some unknown share of those 775 is this cause instead. Parallel calls are the default style for the sessions writing this vault, and the system prompt they run under tells them to batch independent calls. So the retry figure in this tree is inflated by a second, different amount, and the more efficiently a session batches its calls, the more friction it appears to produce.

**Limits.** Three sessions checked by hand, two showing the pattern. This is a mechanism confirmed twice, not a rate. The api-request-blob entry is the host's format and could change or vanish. I did not check whether a blob can also carry `tool_result` blocks with `is_error: true`, which would double-count `tool_error` the same way.

**Evidence rung:** observed. The source is a mechanical recording of the agent's own session plus a grep of the raw file. It grounds usability of this product's feedback channel, not demand.

## History
- 2026-10-17 body edited — The first version said the duplicate copy of each call sat on "one combined line" of the parallel batch. Reading the entry types showed something else: each second copy is inside a host-written `"type":"api-request-blob"` entry, and `extractFriction` reads any entry type. That changes which fixes are available, so the mechanism and litmus sections are corrected here rather than left wrong under a later append.

## 2026-10-17 (later firing) — a third session, 12 of 12

`TRANSCRIPT:b4b069c8-9034-412e-89bd-ed374d22e72b` was the unattended firing that wrote two of this node's solutions. It was filed as **12 friction events, retry ×12, nothing else**. I grepped the raw session file for each `tool_use` id. **All 12 ids appear on exactly two lines.** The second copy is always in a `"type":"api-request-blob"` entry: lines 52/54→60, 74/76/78→83, 90/92/94→97, 104/106→111, 118/120→124. That makes five parallel batches, and every one was copied. The session also made two single calls (lines 36 and 66). Blob entries follow both of them (lines 39 and 71), but neither blob holds the call's id, so neither was double-counted.

**What this adds to the limits above.** The mechanism is now confirmed in three sessions, not two. In those three, every parallel batch (8 of 8) was copied and none of the single calls (0 of 4) were. That is still three files, not a rate. In this session the cause accounts for 100% of the filed friction. So a firing that batches every independent read, as its system prompt tells it to, can come out showing a dozen "struggles" while it struggled with nothing.

_Source: TRANSCRIPT:b4b069c8-9034-412e-89bd-ed374d22e72b, plus a Grep of the session's raw `.jsonl`. Rung unchanged (observed). This grounds the usability of the feedback channel, not demand._

## 2026-10-17 (later firing) — the `is_error` limit above, checked: blobs carry results, and none so far carries an error

The **Limits** paragraph says: "I did not check whether a blob can also carry `tool_result` blocks with `is_error: true`, which would double-count `tool_error` the same way." I checked it with a Grep over every `.jsonl` session file in this vault's project directory.

- **Blobs do carry results.** 13 session files have `api-request-blob` lines that contain a `"tool_result"` block, 59 lines in all.
- **None of those blob lines contains `"is_error":true`.** That held across the whole directory, with 0 matches.
- **Errors and result-carrying blobs do appear in the same sessions.** Three of the 13 files (`70f6e650-…`, `186b60bd-…`, `30bc9037-…`) also hold an `is_error:true` result. In `70f6e650-…` the one error result (line 209, `toolu_0163Ezyv1ZiJTjBhGXDjsscZ`) appears on exactly two lines: the call and its result. No blob copied it.

**What this means for the solutions beneath.** So far the double-count is limited to `retry`. The "copied `tool_result` with `is_error: true`" risk that "Take the host's tool_use id as the identity of a call, and build no notion of a repeated call here" lists as a give-up has not been seen in practice. A builder should still key the error path on `tool_use_id`, because nothing guarantees the host keeps errors out of blobs.

**Limits.** This was a literal string match, so a blob that stored an error as escaped JSON or with different spacing would be missed. The `"id":"toolu_` and `"tool_result"` matches show that blobs are not escaped in the files checked. The check covers one project directory, and only up to today. I did not read how `extractFriction` decides `tool_error`, so whether it keys on `is_error` at all is unverified. Nothing was executed and no rung moved. `ost_check` is withheld on this surface, so this write is unverified by design.

## 2026-10-17 (later firing) — a fourth session: 11 of 12 retries are blob copies, and the twelfth is the parent's cause

`TRANSCRIPT:e14468da-f53b-4327-8b9f-71e87fd40532` was the unattended firing that wrote the `is_error` section above. It was filed as **12 friction events, retry ×12, nothing else**. I grepped its raw `.jsonl` for every `"id":"toolu_…"`.

- **11 of the 12 are this node's cause.** The session made five parallel batches, and every one was copied into a following `"type":"api-request-blob"` entry: lines 64/66→69, 74/76→81, 126/128/130→135, 152/154→157, 175/177→180. That is 11 ids, each on exactly two lines, matching the 11 argument-carrying retries (two `ost_next_work` with `evidence`, seven `ost_read_tree`, two `Grep`).
- **The twelfth is the parent's cause, not this one.** The `ost_ingest_inbox` retry is two real calls with two different ids (`toolu_01AAWP…` on line 31, `toolu_01FzvW…` on line 205): the start-of-pass ingest and the confirm-before-report ingest the loop prescribes. So both causes show up in one session, and they can be counted apart.
- **No single call was copied.** The session made 18 single calls, and none of their ids appears twice.

**Running tally across the four sessions checked.** 13 of 13 parallel batches were copied, and 0 of 22 single calls were. That is still four files from one host version, not a rate. But a session that batches every independent read now reliably produces retry counts this cause has inflated.

_Source: TRANSCRIPT:e14468da-f53b-4327-8b9f-71e87fd40532, plus a Grep of that session's raw `.jsonl` for tool_use ids and entry types. Rung unchanged (observed). This grounds the usability of the feedback channel, not demand. `ost_check` is withheld on this surface, so this write is unverified by design._

## 2026-10-17 (later firing) — a fifth session, and the first parallel batch that was not copied

`TRANSCRIPT:8dfe02f3-d3bd-466a-a391-e511057bfad8` was the firing that wrote the fourth-session section above. It was filed as **8 friction events, retry ×8**. I grepped its raw `.jsonl` for every `"id":"toolu_…"` and every tool `"name"`.

- **6 of the 8 are this node's cause.** Three parallel batches were copied into a following blob line: Grep 76/78→81, Grep 86/88→91, `ost_read_tree` 104/106→110. That covers the four Grep retries and the two `ost_read_tree` retries in the record.
- **2 of the 8 are the parent's cause.** `ost_ingest_inbox` (lines 31, 132) and `ost_next_work` (lines 36, 138) were each called twice with different ids. These are the start-of-pass and confirm-before-report calls the loop prescribes.
- **New: one parallel batch was not copied.** Lines 54, 55 and 56 hold one `ost_read_tree` and two `ost_next_work` calls with an `evidence` argument. All three ids appear only once. In the four earlier sessions, each call in a batch sat on its own line with a result line in between, for example 76/78 with the result on 77. Here the three calls sit on consecutive lines. I did not find out why the host skipped this one. The difference in layout is all I observed.

**Running tally, corrected.** Across five sessions, 16 of 17 parallel batches were copied and 0 of about 32 single calls were. So the "13 of 13" above should no longer be read as "every parallel batch is copied". The copying is common, but not guaranteed. That matters to "Scan only the entries that are conversation turns, so the host's request copies never reach the retry check": a fix that assumes a copy always exists would be wrong. It does not matter to keying on the `tool_use` id, because that fix holds either way.

_Source: TRANSCRIPT:8dfe02f3-d3bd-466a-a391-e511057bfad8, plus a Grep of that session's raw `.jsonl`. Rung unchanged (observed). This grounds the usability of the feedback channel, not demand. `ost_check` is withheld on this surface, so this write is unverified by design._

## 2026-10-17 (later firing) — a sixth session: 12 of 13 are blob copies, and adjacent calls were copied too

`TRANSCRIPT:41381be0-b96c-4c70-8641-344edf4423f7` was the unattended firing just before this one. It was filed as **13 friction events, retry ×13**. I grepped its raw `.jsonl` for every `"id":"toolu_…"`, every `api-request-blob` line and the ingest/ToolSearch call names.

- **12 of the 13 are this node's cause.** The session made four parallel batches, and every one was copied into a following blob line: 51/52/55→59, 75/77/79/81→84, 91/93→98, 105/107/108→113. That is 12 ids, each on exactly two lines.
- **The thirteenth is the parent's cause.** `ost_ingest_inbox` sits on lines 31 and 129 with two different ids. These are the start-of-pass and confirm-before-report calls the loop prescribes.
- **No single call was copied.** Lines 20, 31, 36, 43, 67, 121 and 129 each hold one id, and none of those ids appears twice.

**What this does to the fifth session's open question.** That section found one uncopied batch whose three calls sat on consecutive lines (54/55/56), and offered layout as the only difference it observed. Here two copied batches also contain adjacent calls (51/52 and 107/108). So "adjacent calls are not copied" does not hold as a rule. The one uncopied batch is still unexplained, and it is still the only one.

**Running tally:** 20 of 21 parallel batches copied, 0 of about 39 single calls, across six sessions from one host version. That is not a rate. It also changes nothing about the fixes: keying on `tool_use` id holds whether or not a copy exists.

_Source: TRANSCRIPT:41381be0-b96c-4c70-8641-344edf4423f7, plus three Greps of that session's raw `.jsonl`. Rung unchanged (observed). This grounds the usability of the feedback channel, not demand. `ost_check` is withheld on this surface, so this write is unverified by design._

## 2026-10-17 (later firing): a seventh session, 9 of 10

`TRANSCRIPT:39147a6a-d42c-4e02-b1b0-d302893ca7e0` was filed as **10 friction events, retry ×10**. I grepped its raw `.jsonl` for the `tool_use` ids of the four tools named in the record.

- **9 of the 10 are this node's cause.** It made four parallel batches, and all four were copied into a following `api-request-blob` line: 52/54→58, 66/68→73, 88/90→93, 107/109/111→114. That is 9 ids, each on exactly two lines.
- **The tenth is the parent's cause.** `ost_ingest_inbox` sits on lines 31 and 127 with two different ids: the start-of-pass call and the confirm call that the loop prescribes.
- **No single call was copied.** Lines 36, 80 and 101 each hold an id that appears only once.

**Running tally:** across seven sessions from one host version, 24 of 25 parallel batches were copied and 0 of about 44 single calls were. Nothing new about the mechanism. I'm recording it so the evidence counts as mapped. Later sessions that only repeat this pattern might be better counted in a single line than given a section each, and that call is for a human to make.

_Source: TRANSCRIPT:39147a6a-d42c-4e02-b1b0-d302893ca7e0, plus two Greps of that session's raw `.jsonl`. Rung unchanged (observed). This grounds the usability of the feedback channel, not demand. `ost_check` is withheld on this surface, so this write is unverified by design._

## 2026-10-18 — an eighth session, 7 of 9, and a second uncopied batch

`TRANSCRIPT:47bb76a8-87f2-4bfb-be90-1fb181eaa9c7` was filed as retry ×9. Grep of its raw `.jsonl` for the four tool names in the record: **7 are this node's cause** (batches 51/53→59, 75/77→80, 99/101/103→109, each id on exactly two lines); **2 are the parent's** (`ost_ingest_inbox` 31/127 and `ost_next_work` 36/133, each a different id — the prescribed start and confirm calls). A fourth batch, two `ost_read_tree` calls on **consecutive lines 117/118**, was not copied — the second uncopied batch seen, and like the fifth session's it sits on adjacent lines with no result line between. The sixth session showed adjacency is not sufficient to skip copying, so this is a pattern worth a human's look, not a rule.

Running tally: 27 of 29 parallel batches copied, 0 single calls copied, eight sessions, one host version. One line per further session from here, per the seventh-session suggestion. _Rung unchanged (observed); grounds usability of the feedback channel, not demand. Unverified by design (`ost_check` withheld)._

## 2026-10-18 — ninth session, 17 of 18

`TRANSCRIPT:cb7091af-7d93-496d-872a-8ffb96724258` (retry ×18, tool_error ×1). Grep of its raw `.jsonl` for tool_use ids: **17 are this node's cause**, in four copied batches: 54/56→62, Grep 154/156/158→161, 125/127/129/131→134, and an eight-call `ost_next_work` batch 168–182→187. Each id is on exactly two lines. **1 is the parent's** (`ost_ingest_inbox` 31/206, two ids). Running tally: 31 of 33 parallel batches copied, nine sessions. The eight-wide batch is the largest seen so far, and one firing that batched eight evidence reads was filed as eight struggles. _Rung unchanged (observed). Unverified by design (`ost_check` withheld)._
