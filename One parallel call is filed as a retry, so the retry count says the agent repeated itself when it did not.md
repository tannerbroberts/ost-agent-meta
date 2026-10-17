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

I grepped the raw session file for each event's `tool_use` id. **Every one of the 8 ids appears on exactly two lines.** For example, `toolu_01YPhDz2pr6v1PYvgNMzf4pr` is on lines 56 and 60, and line 77 holds all three `ost_read_tree` ids that had each already appeared on lines 68, 70 and 72. These are not repeated calls. Each is one call, made as part of a parallel batch, which the session file records once per block and then again on one combined line. The agent made zero genuine retries in that session.

The same pattern is in `TRANSCRIPT:a6cedf56-1e19-4ed7-93da-043fa036ab1b`: two parallel pairs, each id on two lines (52/60, 54/60, 66/73, 68/73). A third session, `TRANSCRIPT:015d5a7e-66f4-4c02-b7c1-bb9c91267f3c`, has no duplicated ids at all. Its two retries are the genuine prescribed repeats the parent node describes. So the double-logging only happens for parallel batches, and the two causes can appear separately.

## The mechanism, read from the code

`extractFriction` in `src/adapters/transcript.ts` decides a retry with `` const signature = `${name}:${input}` ``. It never consults the block's `id`. So it cannot tell a call made twice apart from one call written twice. The existing spec hides the problem: the `assistantTool` helper in `test/adapters/transcript.test.ts` gives every call the same id, `"t1"`, so the one retry test ("reports a repeated identical tool call as a retry") can never tell these cases apart either.

## Why this is not the parent, and not its sibling causes

The parent node is about **prescribed** repeats: the loop really calls `ost_next_work` twice, with two different ids, because its procedure says to. This node is about calls that happened **once**. Torres's test, both ways:
- Keying the retry check on the `tool_use` id removes every event here and none of the parent's. Prescribed repeats have different ids, so they still file.
- "A human-edited manifest of loop-prescribed call sequences the harvester suppresses" removes the parent's events and none of these. The calls here take arguments and are not loop-prescribed, so no manifest would name them.

Two of the parent's three solutions, "Drop the retry class entirely and count only events carrying a refusal or an error" and "Take the host's own error flag as the definition of friction instead of authoring one here", would remove both causes, by giving up retry detection entirely. That overlap is real and a human comparing them should weigh it. A narrower fix only exists for this cause.

## Litmus (more than one way to address this?)

Yes: key the retry check on the block id; collapse consecutive transcript entries belonging to one assistant message before scanning; stop inferring retries at all; or keep the inference but label every retry with whether its id was new, so a reader can discount it. Passes.

## Why it costs something

The parent's 2026-10-11 census counts 775 evidence records containing any retry and attributes the class mostly to prescribed repeats. Some unknown share of those 775 is this cause instead. Parallel calls are the default style for the sessions writing this vault, and the system prompt they run under tells them to batch independent calls. So the retry figure in this tree is inflated by a second, different amount, and the more efficiently a session batches its calls, the more friction it appears to produce.

**Limits.** Three sessions checked by hand, two showing the pattern. This is a mechanism confirmed twice, not a rate. How Claude Code writes its transcript is the host's behaviour and could change. I did not check whether `tool_result` blocks are double-logged in the same way, which would also inflate `tool_error`.

**Evidence rung:** observed. The source is a mechanical recording of the agent's own session plus a grep of the raw file. It grounds usability of this product's feedback channel, not demand.
