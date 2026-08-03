---
type: Opportunity
source: 'TRANSCRIPT:5960b7ec-960c-4700-9e0b-2b68c3519e92'
created: '2026-08-03'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed

**The need:** I want to know the file I am about to change is still the file I read, instead of discovering it moved from the edit that fails.

**What was observed.** Six mechanically-captured sessions in eight days each produced the same refusal — `String to replace not found in file` — from an Edit issued against text the agent had read moments earlier: `5960b7ec`, `424486ec`, `4ff7b605`, `995b8ab1`, `0d27cebf`, and `516fdfb8` (which produced the mirror-image form, `No changes to make: old_string and new_string are exactly the same`). Two of them carry the tool's own diagnostic verbatim: *"Edit also tried swapping \uXXXX escapes and their characters; neither form matched, so the mismatch is likely elsewhere in old_string. Re-read the file and co…"* — the tool exhausted its guesses and handed the problem back.

**Why it is not simply a mistake.** Session `424486ec` recorded the cause in the same breath as the symptom. Two Edit refusals, then a clarifying question opening: *"Another process is writing to this repo right now (HEAD moved to the PR #22 merge, and ~14 source files have uncommitted changes touched seconds ago, including a brand-new `pushTargetFor` that …"*. The agent was not misremembering; the file genuinely changed underneath it. Nothing announced that, so the only channel that reported it was a failed write.

**Why it is distinct from what the tree already holds.** [[Two agents sharing my vault can trample each other]] is about two writers corrupting shared vault state — the damage is to the data. This is about a single writer acting on a read that has silently expired — the damage is to the call, and the fix space is different (revalidate before writing, rather than serialize the writers). [[Two thirds of my calls failed, and each one only told me after I made it]] covers learning what *exists* from a refusal; this covers learning that what exists has *changed*.

**Litmus test — more than one way.** Carry a content hash from read to write and refuse on drift with the drift named; subscribe to external writes and invalidate the agent's copy when one lands; edit by anchor or structure rather than literal string match, so formatting churn does not break the address; make the refusal show the current text near the intended site, so one failure resolves the question instead of starting a re-read. Distinct mechanisms with real trade-offs. Passes.

**Placement:** Top-level under the Outcome. It conditions any branch where compute edits files it did not just write, which is most of them.

## Provenance

Distilled from `TRANSCRIPT:5960b7ec-960c-4700-9e0b-2b68c3519e92` — observed behavior, captured mechanically from the agent's own session transcript. Corroborated by five further sessions named above, each read in full this pass. This channel grounds usability, not desirability: it is the agent's own use of its tools, and must not be counted as outside evidence of want.
