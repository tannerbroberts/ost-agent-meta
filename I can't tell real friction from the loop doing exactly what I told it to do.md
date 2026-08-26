---
type: Opportunity
source: 'TRANSCRIPT:98dcaba0-5cd8-4e56-8360-55b58a655cd8'
created: '2026-08-26'
evidence: observed
authorship: machine
---
#Opportunity #unvalidated #evidence/observed
[[Drop the retry class entirely and count only events carrying a refusal or an error]]
[[A human-edited manifest of loop-prescribed call sequences the harvester suppresses]]
[[Take the host's own error flag as the definition of friction instead of authoring one here]]

**The need (operator's voice):** "The friction channel is how the product learns what hurts. Today's record contains two events, and both of them are my agent making the second call the maintenance loop mandates. I want the friction that happened *to* the run separated from the procedure I wrote for it, because right now my most reliably recurring signal is my own instructions."

## What was observed, first-party, this pass

`TRANSCRIPT:98dcaba0-5cd8-4e56-8360-55b58a655cd8` (captured 2026-08-26, mirrored 0d ago) is a complete session record whose entire content is:

- **retry** (`mcp__ost-agent__ost_ingest_inbox`): `{}`
- **retry** (`mcp__ost-agent__ost_next_work`): `{}`

Nothing failed. No tool refused anything. Those two calls are step 5 of the documented maintenance loop, which instructs every pass to "re-call `ost_ingest_inbox`, then `ost_next_work`, to confirm progress". The harvester classifies a second call to the same tool as a `retry` regardless of whether the repeat was prescribed, so a pass that follows its own procedure manufactures a friction record by doing so.

The same session-set shows the softer form: `TRANSCRIPT:24326ff1-58af-41a6-a84f-82d321680f4a` files a `retry` of `TaskOutput` with `block: true` — blocking on a backgrounded task's output, which is the form this workspace's own standing correction tells sessions to use instead of chained sleeps. Prescribed behaviour, filed as friction.

## Why this is not the sibling beside it

"The friction channel fills with my own typos, so the signal I wanted is buried" names noise made of *mistakes* — shell-quoting slips, globs that matched nothing, an edit whose search string had drifted. This node names noise made of *compliance*, and the distinction is load-bearing because the four candidate fixes listed under that sibling do not reach this case:

- *Classify by whether the event touches the product's own surface* — `ost_ingest_inbox` and `ost_next_work` **are** the product's own surface, so this filter promotes these events rather than dropping them.
- *Weight recurrence over incidence* — this repeats on every single pass by construction, so a recurrence weighting files it every time and ranks it top.
- *Fold self-corrected errors into a counted summary* — nothing was in error and nothing was corrected, so there is nothing to fold.
- *Let a session mark its own friction as meaningful* — the only one that could work, and only because it routes around the classifier entirely.

A solution addressing one sibling therefore does not address the other, and one of that sibling's candidates actively worsens this one. Torres's test passes: these are two needs, not two phrasings.

## Litmus test (more than one way to address this?)

Yes, and they trade off against each other: teach the harvester which call sequences are loop-prescribed and exclude them; require an event to carry a failure or refusal before it counts as friction at all, so a bare repeat never files; have the loop declare its own prescribed steps in-band so the classifier reads intent rather than inferring it from call shape; or drop the `retry` class entirely and keep only `tool_error`, accepting the loss of genuine retry-after-failure signal. Passes.

## Why it costs something

`ost_next_work` reported 415 unmapped evidence records at the head of this pass, and the sibling node's own 2026-08-02 census put the channel's yield at 5 of 29. Every compliance-shaped record is read in full by a pass before being declined, and — as that census also records — nothing in the tool surface can mark an item considered-and-declined, so the same record is read and declined again on every future firing. This is the one noise class that is generated deterministically rather than by accident, which makes it both the cheapest to remove and the most expensive to leave.

**Evidence rung:** `observed` — the source is a mechanical transcript recording of the agent's own session, not a self-report. It grounds usability of this product's own feedback loop; it is not outside-user demand data and must not be counted as evidence that anyone wants this.

**For a human to review:** whether a prescribed repeat is genuinely *never* friction. A loop forced to re-call because the first call returned something unusable would look identical in the record, and this node assumes that case is rare enough to trade away. That assumption is the agent's and is worth checking.

## The mechanism, read first-party from the code (2026-08-26)

`ost_read_repo` on `src/adapters/transcript.ts` settles how a `retry` comes to exist, and it is simpler and more deterministic than the observation alone suggested. Inside `extractFriction`, every `tool_use` block is reduced to `` const signature = `${name}:${input}` `` where `input` is `JSON.stringify(block.input ?? {})`. If that exact string has been seen before in the session, a `retry` event is pushed; otherwise the signature is remembered.

Three consequences follow directly, and they are facts about the code rather than inferences from the record:

1. **A repeat fires on identical arguments, and both loop-closing calls take none.** `ost_ingest_inbox` and `ost_next_work` are invoked with `{}`, so their signatures are `mcp__ost-agent__ost_ingest_inbox:{}` and `mcp__ost-agent__ost_next_work:{}` on the first call and byte-identical on the second. Step 5 of the maintenance loop therefore emits two `retry` events on every well-behaved pass, by construction. The record this node is sourced to is not a fluke; it is the guaranteed output.
2. **The `retry` branch is the one classifier that never consults whether anything failed.** Every other kind in this adapter is grounded in something observable: `tool_error` and `permission_denied` are only reached under `block.is_error === true`, and `interruption` matches text the host wrote. `retry` alone is derived purely from call shape, with no reference to the outcome of the earlier call.
3. **The better a pass complies, the more friction it appears to generate.** A pass that skips the loop's confirmation step files nothing here; a pass that follows the instructions files two. The channel's incentive runs backwards.

This raises the node's grounding from "one record read in full" to "the record plus the rule that produced it", and it is what makes the litmus candidates below concrete rather than speculative. It does not raise the evidence rung: reading the source confirms the mechanism, not that anyone outside this project cares.

_Source: this pass's own `ost_read_repo` read of `src/adapters/transcript.ts`. First-party observation of the repository. No test was run and no result is recorded — the code is reported as read, not as executed._
