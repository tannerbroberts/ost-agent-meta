---
type: Solution
source: 'TRANSCRIPT:98dcaba0-5cd8-4e56-8360-55b58a655cd8'
created: '2026-08-26'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[The founder will keep a manifest of prescribed call sequences current as the loop's steps change]]

**Variation dimension: automated-vs-manual. Position taken: the matching is automated, the definition of "procedure" is deliberately left manual.**

A small declarative manifest lists the call sequences that are procedure rather than pain — `ost_ingest_inbox` followed by `ost_next_work` at the close of a pass; a blocking `TaskOutput` on a task the same session started. The harvester matches every candidate friction event against it and suppresses the matches automatically, with no judgement at harvest time. What stays manual is the list itself: a person edits it, because what counts as prescribed is set by the ruleset the person writes, and the ruleset changes.

**Why the manual half is the point, not a shortcut.** The loop's procedure is not a property of the code — it lives in the skill text and the firing prompt, both of which a human rewrites. Any mechanism that infers "prescribed" from the code would be reading the wrong artifact and would go silently stale the next time the loop's steps change. Making the list an artifact a person edits keeps it in the same place as the thing it describes, and a manifest entry that no longer matches anything is visible in a way an inference is not.

**Against the siblings.** Unlike deleting the `retry` class, this keeps genuine retry-after-failure signal intact — a repeat that is not on the list still files. Unlike adopting the host's error flag, the suppression rule is authored here and can encode this product's own procedure, which no upstream signal knows anything about.

**What it costs.** A maintenance burden with a known failure mode: this project's own tree already records that artifacts asking for recurring founder input are the ones that go unmaintained, and there is a live assumption elsewhere on exactly that question ("The founder will actually maintain a highlight criteria note over time"). A stale manifest fails in the dangerous direction — it keeps suppressing a sequence that has stopped being procedure, so real friction goes missing rather than merely unfiltered.

**What would make this the wrong pick.** If the prescribed sequences turn out to be few and stable, a manifest is ceremony around two hard-coded rules. If they turn out to be many and fast-changing, nobody will keep it current. It is the right pick only in the middle case.

Unvalidated — a human to review.

## Definition of done — and it is not a command

"Count how many recurring-input artifacts the founder has actually kept current, before asking for another"

There is deliberately no instrument here. The belief this candidate rests on is whether one specific person keeps one more list current, and the bar is: at least 2 of the founder's existing recurring-input artifacts were edited within 30 days of the change they were meant to track. A script can gather the timestamps that start the conversation; it cannot supply the half that decides the answer, which is why an artifact that went stale went stale.

The test title is quoted rather than wikilinked on purpose: its one backlink belongs to its parent assumption.

**Sequencing this candidate against its siblings:** this is the cheapest of the three to build and the only one that can fail after it ships, silently, by suppressing a sequence that stopped being procedure. So the viability answer should come before the build, not after — and if it comes back below the bar, the sibling that deletes the repeat inference outright is the default, because it asks nobody for anything.

**Lane note for a human:** this test was created in the humans-required lane at creation time. `ost_flag_humans_required` is withheld on the unattended surface, so if the lane ever needs changing it is `ost-agent lane --set`.

## First-party instance: a friction-free firing that manufactured its own friction record (2026-08-28)

This candidate was ideated from the theory that the harvester counts prescribed procedure as friction. That is no longer theory. The evidence record this sweep captured at ingest — `TRANSCRIPT:6d96802b-a693-425d-97c4-3eb0db903f94`, mirrored 0d ago — is that failure in its purest available form, and it is worth stating because it changes what this branch is worth rather than merely restating it.

**The record, in full.** Two friction events, both `retry`, both with empty arguments:

- retry (`mcp__ost-agent__ost_ingest_inbox`): `{}`
- retry (`mcp__ost-agent__ost_next_work`): `{}`

Nothing else. No `tool_error`, no interruption, no denial. The signal-to-noise on that record is 0 of 2.

**Why those two and no others, read off the code rather than inferred.** Verified this pass with `ost_read_repo` against `src/adapters/transcript.ts`. `extractFriction` builds a signature as `` `${name}:${JSON.stringify(input)}` ``, keeps a `seenCalls` set, and pushes a `retry` on the second appearance of a signature — with no reference to any `tool_result`, `is_error`, or outcome of the first call. Both of these tools take no arguments, so every call either of them makes has the identical signature `{}`. The unattended loop's own prompt prescribes calling `ost_ingest_inbox` then `ost_next_work` at step 1, and re-calling both at step 5 to confirm progress. The second pair is therefore guaranteed to trip the repeat detector. The procedure the firing was instructed to follow is the generator.

**The part that makes this more than noise.** `TranscriptSource.fetchSince` contains `if (events.length === 0) continue` — a session with no friction produces no evidence item at all. So on a firing that followed its instructions and hit nothing wrong, these two manufactured retries are not a contaminant in a real record; they are the entire reason a record exists. A clean run does not stay silent. It files a document titled "Session friction" whose contents are the loop obeying itself.

**The compounding cost, which is the argument for doing something here.** Each such record then joins `unmappedEvidence` and stays there, because there is no genuine need underneath it to distil and mapping it would only duplicate this branch. That queue stood at 441 items on this sweep. Every firing that goes well adds one more, and the number an operator reads as discovery debt is inflated by the loop's own well-behaved passes. The channel does not merely get noisier over time; the backlog that measures how far behind discovery is grows fastest when nothing is wrong.

**What this does not establish, stated so a later reader does not over-read it.** It is one record plus a mechanism, not a census. It does not measure what share of the 441 are of this kind, and the share is what decides whether a manifest is ceremony or a real filter — the sibling test "A repeated no-argument call with no error files nothing, while a repeat whose result is an error still files" names that census as the open question and it stays open. Nor does it bear on this candidate's own sharpest risk, which is whether the founder maintains the manifest; that belief is untouched by any of the above. And a caveat that cuts against the finding: a call carrying arguments has a different signature, so a firing that reads an evidence body or passes `since` does not trip the detector on that call. This sweep did exactly that, which is a reminder that the generator fires on the no-argument tools specifically, not on every repeat.

**Self-demonstrating, and offered as a check.** This pass opened with `ost_ingest_inbox` and `ost_next_work`, both no-argument, and closes by calling both again as step 5 instructs. Its own transcript should therefore be harvested into a record containing the same two `retry` events. Whoever reads this next can confirm the mechanism at no cost by looking for it.

_Source: this pass's own `ost_ingest_inbox` output, the evidence body served by `ost_next_work`, and a first-party read of `src/adapters/transcript.ts` via `ost_read_repo`. Observed behaviour of this product; it grounds usability, not desirability. No test was run and no result is recorded._
