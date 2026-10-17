---
type: Opportunity
source: 'TRANSCRIPT:8275c757-fcf0-46d1-9d35-bfab1fdd33f9'
created: '2026-10-17'
evidence: observed
authorship: machine
---
#Opportunity #unvalidated #evidence/observed

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
