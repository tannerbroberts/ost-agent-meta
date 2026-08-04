---
type: Opportunity
source: 'TRANSCRIPT:5960b7ec-960c-4700-9e0b-2b68c3519e92'
created: '2026-08-03'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed
[[Carry a content hash from read to write and refuse on drift, naming what drifted]]
[[Watch the working tree and invalidate the agent's copy the moment an external write lands]]
[[Make the refusal show the text that is actually there now]]

**The need:** I want to know the file I am about to change is still the file I read, instead of discovering it moved from the edit that fails.

**What was observed.** Six mechanically-captured sessions in eight days each produced the same refusal — `String to replace not found in file` — from an Edit issued against text the agent had read moments earlier: `5960b7ec`, `424486ec`, `4ff7b605`, `995b8ab1`, `0d27cebf`, and `516fdfb8` (which produced the mirror-image form, `No changes to make: old_string and new_string are exactly the same`). Two of them carry the tool's own diagnostic verbatim: *"Edit also tried swapping \uXXXX escapes and their characters; neither form matched, so the mismatch is likely elsewhere in old_string. Re-read the file and co…"* — the tool exhausted its guesses and handed the problem back.

**Why it is not simply a mistake.** Session `424486ec` recorded the cause in the same breath as the symptom. Two Edit refusals, then a clarifying question opening: *"Another process is writing to this repo right now (HEAD moved to the PR #22 merge, and ~14 source files have uncommitted changes touched seconds ago, including a brand-new `pushTargetFor` that …"*. The agent was not misremembering; the file genuinely changed underneath it. Nothing announced that, so the only channel that reported it was a failed write.

**Why it is distinct from what the tree already holds.** [[Two agents sharing my vault can trample each other]] is about two writers corrupting shared vault state — the damage is to the data. This is about a single writer acting on a read that has silently expired — the damage is to the call, and the fix space is different (revalidate before writing, rather than serialize the writers). [[Two thirds of my calls failed, and each one only told me after I made it]] covers learning what *exists* from a refusal; this covers learning that what exists has *changed*.

**Litmus test — more than one way.** Carry a content hash from read to write and refuse on drift with the drift named; subscribe to external writes and invalidate the agent's copy when one lands; edit by anchor or structure rather than literal string match, so formatting churn does not break the address; make the refusal show the current text near the intended site, so one failure resolves the question instead of starting a re-read. Distinct mechanisms with real trade-offs. Passes.

**Placement:** Top-level under the Outcome. It conditions any branch where compute edits files it did not just write, which is most of them.

## Provenance

Distilled from `TRANSCRIPT:5960b7ec-960c-4700-9e0b-2b68c3519e92` — observed behavior, captured mechanically from the agent's own session transcript. Corroborated by five further sessions named above, each read in full this pass. This channel grounds usability, not desirability: it is the agent's own use of its tools, and must not be counted as outside evidence of want.

## Corroborating sessions (2026-07-29 → 2026-07-30)

- `TRANSCRIPT:424486ec-3489-4b53-8e2b-012232d221ab` — two consecutive `String to replace not found in file` errors, then the run stopped to ask the human: *"Another process is writing to this repo right now (HEAD moved to the PR #22 merge, and ~14 source files have uncommitted changes touched seconds ago, including a brand-new `pushTargetFor`…)"*. This is the clearest instance captured: the failed edit was the detector, and the run had to reason backwards from it to work out that a concurrent writer existed.
- `TRANSCRIPT:995b8ab1-5e55-4a5c-b05d-aaed9e1d7538` — `String to replace not found in file`, with the tool volunteering that it also tried swapping `\uXXXX` escapes and neither form matched.
- `TRANSCRIPT:4ff7b605-da1d-4f2e-8c05-ec6408118837` — same failure against `(!blocksDone || allOpenUnknowns.length === 0);`.

What the three together add: the failure mode is indistinguishable at the point of failure from an ordinary stale-string mistake. In two of the three the run treated it as its own error and re-read the file; only in the third did it work out that something else was writing. The cost is not the failed edit, it is the misattribution — and one of the three cost a human interruption to resolve.

Evidence class is observed behaviour of this agent using its own harness — usability, not demand.

## Four failed edits across three sessions, and one session that caught the cause in the act

The `Edit` failures captured in the transcript channel:

- `TRANSCRIPT:424486ec-3489-4b53-8e2b-012232d221ab` — two consecutive *"String to replace not found in file"*, the second carrying the harness's own diagnosis: *"Edit also tried swapping \uXXXX escapes and their characters; neither form matched, so the mismatch is likely elsewhere in old_string. Re-read the file and co…"*
- `TRANSCRIPT:995b8ab1-5e55-4a5c-b05d-aaed9e1d7538` — the same failure, same escape-swap note
- `TRANSCRIPT:4ff7b605-da1d-4f2e-8c05-ec6408118837` — *"String to replace not found in file … (!blocksDone || allOpenUnknowns.length === 0);"*
- `TRANSCRIPT:516fdfb8-bab1-41a4-b1e5-92fde97bd90d` — the inverse symptom: *"No changes to make: old_string and new_string are exactly the same"*

**Why `424486ec` is the load-bearing record.** Its third friction event is a clarifying question the agent asked immediately after the two failed edits, and it names the cause out loud: *"Another process is writing to this repo right now (HEAD moved to the PR #22 merge, and ~14 source files have uncommitted changes touched seconds ago, including a brand-new `pushTargetFor` that…"*. That is this node's mechanism, observed rather than inferred — a concurrent writer moved the file between the read and the edit, and the failed edit is exactly how it was discovered. The agent then had to stop and ask, so the cost was not one wasted call but the whole run.

That record is also evidence for [[Two agents sharing my vault can trample each other]], and the two nodes are not the same claim: this one is about a *stale read* discovered at write time regardless of who moved the file, and that one is about two agents in one vault specifically. `424486ec` happens to be an instance of both.

**The escape-swap detail is worth keeping.** In two of the four the harness reports it tried matching both the `\uXXXX` escape and the literal character before giving up. So the tooling already does one round of guessing about *why* the string did not match, and the guess it offers is not the one that was right here. A hash or mtime check at read time would have named the actual cause in both — which is [[Replay captured sessions to count how often a hash guard would refuse a good write]], already instrumented.

**The fourth record is not the same failure.** *"old_string and new_string are exactly the same"* is a no-op edit, not a stale read. It is listed for completeness and should not be counted toward this node.

_Provenance: four friction records from the transcript adapter, machine-captured, no narrator. Observed behavior of this product's own agent; grounds usability, not desirability. Unvalidated — for human review._
