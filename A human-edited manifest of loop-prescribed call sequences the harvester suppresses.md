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

## The prediction was checked and held (2026-08-28 sweep)

The 2026-08-28 section above closed by offering its own transcript as a free check: a well-behaved firing should be harvested into a record containing nothing but the loop's own prescribed `retry` events. This pass performed that check at ingest and the prediction held.

`TRANSCRIPT:ec918ca1-7f8d-453c-81f0-2e1e977e87f0`, captured 0d ago, consists of **5 friction events, all `retry`, all with empty arguments**: `ost_ingest_inbox` ×2 and `ost_next_work` ×3. No `tool_error`, no interruption, no denial. Signal-to-noise 0 of 5 — a firing that hit nothing wrong, filing a document titled "Session friction" whose entire contents are the loop obeying its own step 1 and step 5.

This is a second independent instance, from a different session than the one that generated the theory, so the mechanism is now confirmed rather than proposed. It is still not the census: two records is not a share of 445, and the share is what decides whether a manifest is a filter or ceremony. What it does narrow is the shape — the generator produces records that are *entirely* noise rather than noise mixed into real signal, which means a suppression rule that dropped them would remove whole records from the queue rather than merely tidying them.

One contrast worth recording alongside it, because it cuts the other way. The other record this pass captured, `TRANSCRIPT:cf2cef94-0aee-4647-80e0-9d64dbe0e18d`, was 9 events of which 7 were genuine `tool_error`s carrying real findings — and its 2 `retry` events were *also* meaningful, being re-issues of a wait that had just expired. So the repeat inference is not uniformly wrong: a repeat of a command carrying arguments can be exactly the signal worth keeping, and this pass mapped a new opportunity out of one. Any rule built here must suppress the no-argument prescribed pair without taking the argument-carrying repeats with it, which is the distinction the sibling test "A repeated no-argument call with no error files nothing, while a repeat whose result is an error still files" already pins.

_Source: this pass's own `ost_ingest_inbox` output and the two evidence bodies served by `ost_next_work`. Observed behaviour of this product; grounds usability, not desirability. No test was run and no result is recorded._

## 2026-08-29 — the cheap mitigation does not cover this node's failure case

Kept short on purpose: this node is already 10,000 characters and two of its sections say much the same thing. Only what is new is below.

**Third data point on the compounding cost.** The queue this node measured at 441 (2026-08-28) and 445 (later the same day) stood at **457** on 2026-08-29. Of the two records this sweep ingested, `TRANSCRIPT:29ee50b7` is the pure-noise shape exactly — 2 events, both `retry`, both no-argument (`ost_ingest_inbox`, `ost_next_work`), no `tool_error`. The other, `TRANSCRIPT:8910f58f`, is the contrasting case this node already flags as must-not-suppress: 13 events, 11 genuine `tool_error`s, and its 2 `retry` events were argument-carrying re-issues of an expired wait, from which this pass distilled a new Opportunity. So the 1-of-2 split matches the shape the 2026-08-28 sections describe, and the census remains uncounted.

**The finding that changes the sequencing argument.** Read with repo sight this pass, `test/evidence/age-out-preserves-novel.test.ts` shows the age-out mechanism is built and its knob, `evidence.ageOutDays`, is unset on this vault — which is why `agedOutEvidence` is `{ count: 0, oldest: null }` against 457 listed items. It is tempting to read that as a one-line fix that makes this candidate unnecessary. It is not, and the spec says why: the implemented rule is **age AND redundancy with a signature some node has already cited** — "AGE ALONE MAY NEVER COLLAPSE AN ITEM," in the spec's own words, with a fixture built so that pure age fails it.

The self-manufactured friction records have no already-mapped signature to be redundant with, precisely because — as this node argues at length — there is no genuine need underneath them to distil, so no Opportunity ever cites one. **Enabling `evidence.ageOutDays` would therefore leave exactly these records individually listed forever.** The cheapest available mitigation misses this node's failure case by construction, which strengthens rather than weakens the argument for suppressing at harvest time.

**What this does not settle.** Nothing here touches this candidate's sharpest risk — whether the founder keeps the manifest current — which stays where the parent assumption has it. And the claim above is read off the spec's assertions, not from a run: no test was executed and no result is recorded.

## 2026-08-30 — the census this node has called open three times, counted over a 25-record sample

Kept short, per this node's own convention. Only what is new.

**The question.** Three sections above say the share of the queue that is self-manufactured is what decides whether a manifest is a filter or ceremony, and that the share is uncounted. This pass counted it over the 25 records `ost_next_work` showed (of 464 total), using each record's own event tally, and read 4 record bodies in full to check what the `retry` lines actually are.

**The numbers.**

- **Whole-record noise: 3 of 25 (12%).** Records whose entire contents are prescribed no-argument retries — `01e55025` (2 events), `0e24ead9` (2), `0ffc6652` (1). All three read in full; all are `ost_ingest_inbox` and/or `ost_next_work` with `{}` and nothing else.
- **Records carrying at least one `retry`: 22 of 25 (88%).**
- **Records carrying at least one genuine `tool_error`: 22 of 25 (88%).**
- **Event mix across the sample: 61 `tool_error` to 38 `retry` — retries are 38% of all friction events.**
- **The contamination is line-level, not record-level.** `08f7d98f` is 4 events: two real `tool_error`s (a `Glob` denied the read grant for the product repo, twice) followed by the identical prescribed pair. The generator fires inside otherwise-genuine records, not only in empty ones.

**What this does to the argument, and it cuts against this candidate's headline.** The compounding-cost case built above rests on queue *length* — 441, then 445, then 457, now 464. Suppression fixes ~12% of that. A queue of 464 becomes a queue of ~408, and the operator still cannot page past a cap of 25. **The queue is not long because of self-manufactured records; it is long because 88% of records contain genuine `tool_error`s that no Opportunity has ever been distilled from.** That is discovery debt, not noise, and no suppression rule touches it.

**What suppression would genuinely buy, restated honestly.** Signal-to-noise *within* a record, not queue length. A reader of a mapped record would stop seeing two lines of the loop obeying itself under every real finding. That is a real improvement and a much smaller one than "the backlog grows fastest when nothing is wrong" implies.

**Limits of this count, stated so it is not over-read.** The 25 are the unfiltered head of 464, ordered by id, not a random sample — the very defect the sibling window candidate names. So this is a census of the head, and the head may not represent the tail. 4 of the 22 retry-carrying records were opened; the other 18 are inferred from their event tallies and could contain argument-carrying repeats, which this node already establishes can be genuine signal. No test was run and no result is recorded.

_Source: this pass's own `ost_next_work` sweep response and four evidence bodies served by it. Observed behaviour of this product; grounds usability, not desirability._

## 2026-08-30 — one qualification to the count above, from a fifth body read

Two more records were opened after the section above was written, and one of them cuts against it. Recording it here rather than leaving the number to be read as cleaner than it is.

- **Supporting.** `030e5db3` carries 5 `retry` events and every one is the prescribed no-argument pair — `ost_ingest_inbox` ×3, `ost_next_work` ×2. The highest retry count in the sample is entirely the generator. Its 4 `tool_error`s are all permission denials on tools withheld from that firing (`ost_flag_humans_required`, `ost_check`, `ost_status`, and a `Glob` read grant on the product repo).
- **Qualifying.** `09ec7cd2` carries a `retry` on `Write` with a full argument payload — a genuine repeat of a real write to the build loop's report file, not procedure. So the corpus does contain argument-carrying repeats that must not be suppressed, exactly as this node's own "must-not-suppress" caveat predicts. The claim above should read **5 of 6 sampled retry-sets were prescribed-only**, not 4 of 4 with the rest inferred.

Nothing else about this node changed, and the 12% whole-record figure is unaffected — `09ec7cd2` was already counted on the genuine-signal side.

## Issues
- 2026-08-30 2026-08-30 unattended sweep — the mechanism behind this node's own lane note, read off the source rather than inferred. This node records that its test "was created in the humans-required lane at creation time" and that `ost_flag_humans_required` is withheld on the unattended surface. What it did not know is why that combination makes the node reappear in `solutionsMissingInstruments` on every pass regardless: that function in `src/eval/buildable.ts` applies no lane check at all, while `testsAwaitingVerification` two functions below it in the same file does (`if (n.lane === CAUTIOUS_LANE) continue;`). This node's test was read directly this pass and does carry `lane: humans-required` in frontmatter — the label is present and the bucket ignores it. So the census entry is not a judgement about this node; it is a queue that cannot express the decision this node already made. Distilled into a new Opportunity beneath "The pass never says it is done, so I can't tell when to stop paying for compute" rather than argued here, and named in plain text so this node keeps its single backlink: "Work I already decided needs a person comes back every pass as work I failed to do". Nothing else about this node changed — its humans-required Definition of done, its 12% whole-record census and the qualification beneath it all stand unaltered, and no instrument was set.

## 2026-08-31 — the 88% figure re-measured by reading records instead of counting tallies, and it does not mean what the section above took it to mean

Kept short, per this node's own convention. Only what is new.

**The claim being corrected.** The 2026-08-30 census section concludes: "The queue is not long because of self-manufactured records; it is long because 88% of records contain genuine `tool_error`s that no Opportunity has ever been distilled from. That is discovery debt, not noise, and no suppression rule touches it." That section states its own method honestly — 22 of 25 records were scored from their event *tallies*, with only 4 bodies opened. A tally can say a record carries a genuine tool error. It cannot say whether the error's *signature* is already on the tree, and those are different questions.

**What this pass did.** Opened 7 records in full, spanning 2026-08-17 to 2026-08-31: `134bad7e`, `1329bda4`, `1eed544a`, `10002eba`, `0e0cd6f3`, `132bb394`, `6e1984b2`. 26 `tool_error` events between them. Each distinct signature was then traced against the tree by reading node bodies.

**The numbers.**

- **`File has not been read yet` — 13 of 26 (50%).** Present in 6 of the 7 records. Already distilled, and corpus-censused at 416 events across 221 sessions on "The file changed after I read it, and the failed edit is how I find out".
- **Signatures already mapped and corpus-counted — 22 of 26 (85%).** The 13 above, plus `No such file or directory` (3 here, 63 corpus-wide), `InputValidationError` on Read (3 here, 46 corpus-wide), and Monitor's multi-operation approval refusal (2 here, 8 corpus-wide — three solutions already sit under it).
- **Singletons not traced to any node — 4 of 26 (15%).** A zsh glob miss, `Cannot find module './src/security/tools.js'`, a `TypeError … reading 'required'`, and `ScheduleWakeup: prompt is required when stop is not true`. One occurrence each in this sample; no claim is made that they are unmapped, only that this pass did not find them.
- **New needs distilled from all 7 records: zero.**

**Why this changes the repair rather than the size of the problem.** "Carries a genuine tool error" and "carries an undistilled need" were treated as the same predicate, and on this sample they come apart almost completely. The queue is not mostly discovery debt. It is mostly **records whose signature is already mapped, which are never retired once mapped** — a third mechanism, distinct from both the self-manufactured noise this node is about and the debt the section above inferred. That the tree cannot retire them is not a guess: both the drift node's census and this node's own sections record that citing a record does not clear it from `unmappedEvidence`.

**The consequence that points at a mechanism already built, and it flips the 2026-08-29 conclusion by half.** That section argued `evidence.ageOutDays` "would leave exactly these records individually listed forever", because the implemented rule is age AND redundancy with a signature some node has already cited, and the self-manufactured records have no cited signature. That reasoning is sound *for this node's own failure case* and is unaffected. What it obscures is the other side of the same predicate: on this sample 85% of tool errors carry signatures a node **has** cited, so the knob the section dismissed is aimed squarely at the bulk of the queue even though it misses the 12% this node cares about. The two findings are compatible and were read as one.

**Limits, stated so this is not over-read.** 7 records is a small sample and they were chosen for high event counts, which over-weights busy sessions. The signature-to-node tracing was done by reading node bodies, not by grep, so a mapped signature could have been missed and counted as a singleton — that error runs in the direction of *understating* how much of the queue is already mapped. The age-out claim in the paragraph above rests on the 2026-08-29 section's description of `test/evidence/age-out-preserves-novel.test.ts` and not on a first-party read of the implementation; this pass read `src/ost/ageing.ts` and found it to be a different, replay-only module that by its own docstring "changes what a live sweep reports" in no way, so the live age-out path was not verified here and someone should confirm it before turning the knob.

_Method: 7 evidence bodies via `ost_next_work({evidence})`, node bodies via `ost_read_tree`, and `ost_read_repo` reads of `src/ost/ageing.ts` and `src/knowledge/instruments.ts` in full. Nothing executed, no rung moved, no instrument set, no status changed. Observed behaviour of this product's own agent — it grounds usability, not desirability, and is not evidence that anyone wants anything._

## 2026-08-31 — the errand left open above is closed (pointer only)

Four lines, on purpose: this node is already 23,000 characters and the finding belongs on the node it is about, not here.

The 2026-08-31 section above ends by flagging that `src/ost/ageing.ts` turned out to be replay-only, "so the live age-out path was not verified here and someone should confirm it before turning the knob." A later firing the same day confirmed it and recorded the result on "An unmapped item ages out of the queue into a standing backlog line". The short version: `test/evidence/age-out-preserves-novel.test.ts` drives `computeNextWork` from `src/mcp/next-work.js` — the production sweep entry point — with the knob as its sixth argument, so the age-AND-redundancy rule this node reasons about is the live one and the caveat is discharged.

One thing that node adds which changes the advice here: `src/ost/ageing.ts` implements a *different* rule (N untouched passes, reset by a changed signature), so it cannot be used to preview what `evidence.ageOutDays` would bury. Nothing on this node changed, and its own conclusion is unaffected — the knob still misses the self-manufactured records this candidate is about, because they have no cited signature to be redundant with.

## 2026-08-31 — the census, measured over all 534 records instead of a head of 25

Kept short, per this node's convention. Only what is new.

**Why this is not the 2026-08-30 section again.** That section counted the 25 records `ost_next_work` showed, and named its own limit precisely: "the 25 are the unfiltered head of 464, ordered by id, not a random sample… the head may not represent the tail." This pass had native read access to the vault's own `.ost-agent/evidence/` directory and counted the tail as well. Same question, whole denominator.

**The numbers, over 534 transcript evidence records on disk (mapped and unmapped alike).**

- **Records with no `tool_error` at all — 78 of 534 (14.6%).** Counted from each record's own header parenthetical reading `(retry ×N)` with no `tool_error` term.
- **Of those 78, exactly 2 carry an argument-bearing retry** (`da806545`, `414d3daa`), so they are genuine repeats rather than procedure.
- **Whole-record self-manufactured noise: 76 of 534 (14.2%).** Every event a no-argument retry. A spot check of the no-argument retry lines found the tool name is always `ost_ingest_inbox` or `ost_next_work` and never anything else — the pair this loop's own prompt prescribes at step 1 and again at step 5.
- **Records carrying at least one argument-bearing retry: 197 of 534 (36.9%).**

**What holds, and what is new.** The 12% head-of-25 estimate holds up: 14.2% over the full corpus. So the 2026-08-30 conclusion is unchanged — suppression takes 534 records to ~458 and does not explain why the queue is long. What is new is the second figure, which no prior section has: **the must-not-suppress class is 197 records, over a third of the corpus.** This node already warns that "a stale manifest fails in the dangerous direction" and that any rule "must suppress the no-argument prescribed pair without taking the argument-carrying repeats with it." That caveat now has a denominator against it, and it is a large one — the blast radius of a mis-scoped suppression rule is 37% of the corpus, not a handful of edge cases. Whoever builds this should treat the no-argument condition as load-bearing rather than incidental.

**Limits.** Counts are per-record, not per-event: a record is scored by whether it contains a class of event, so this says nothing about the event mix inside the 197. The retry-only set was identified from header parentheticals rather than by parsing each event list, so a malformed header would be miscounted. The claim that no-argument retries are only ever the prescribed pair rests on a 40-line sample of those lines, not on all of them. And 534 is every transcript record on disk, which is a larger denominator than the 508 unmapped items the sweep reports — the two numbers answer different questions and should not be differenced.

_Method: `Glob` and `Grep` over `.ost-agent/evidence/` in this vault, plus this pass's own `ost_next_work` sweep. Nothing executed against the product repo, no rung moved, no instrument set, no status changed. Observed behaviour of this product's own agent — it grounds usability, not desirability._

## 2026-08-31 — the generator observed across two consecutive firings, and a third class that is avoidable (later firing)

Four lines, per this node's convention. Only what is new, and it is prospective rather than another census.

**The prospective check.** Every count on this node is retrospective — a corpus already on disk. This pass read all three records captured at its own ingest, in full, and scored them before doing anything else: `e95f871e` (2 events), `79b70e58` (3), `c2aab3a1` (7). **Twelve events, zero new needs.** Every signature was one this tree has already mapped and counted — read-before-write, the Glob read-grant denial, the prescribed no-argument pair, a missing module, and Monitor's multi-operation refusal. That is the "already mapped, never retired" mechanism this node's 2026-08-31 section infers from a 7-record sample, confirmed forward on the next three arrivals rather than backward.

**The generator caught in the act, across firings.** `79b70e58` consists of a prior firing's `Glob` denial on `/Users/tanner/dev/OST-Agent` plus the prescribed `ost_ingest_inbox`/`ost_next_work` pair. This firing hit the identical `Glob` denial, so the next harvest will file a record of this pass recording that a previous pass was denied. The queue is not merely failing to retire mapped records; on this signature it is generating one per firing about the same fact.

**And this class, unlike the prescribed pair, is avoidable — which no prior note says.** The denial is not a missing capability. `ost_read_repo` reads that same repository fine and was used four times this pass to list `test/`, `src/ost/` and `src/cli/` and to read node-relevant source. What it cannot do is *search*, which is why the 2026-08-31 sections on "Work I already decided needs a person comes back every pass as work I failed to do" correctly record `Grep` as shut. So the honest split is: a firing reaching for `Glob`/`Grep` to **list or read** the product repo is burning a call and minting an unretirable record for something `ost_read_repo` already grants; a firing reaching for it to **search** is hitting a real gap. Both currently produce the same friction line, so the corpus cannot distinguish an avoidable denial from a blocking one — and only the second kind is evidence of anything.

**Limits.** Three records is the arrival batch, not a sample of the 510 — it is a forward check on a mechanism established elsewhere, not a rate. The avoidability claim rests on this pass's own four successful `ost_read_repo` calls against the repo `Glob` was denied on; it does not establish that every past denial had a read-only substitute, only that this one did. No test was run, no rung moved, no instrument set, no status changed, and no node was created.

_Source: this firing's own `ost_ingest_inbox` output, three evidence bodies via `ost_next_work({evidence})`, and four `ost_read_repo` calls. Observed behaviour of this product's own agent — it grounds usability, not desirability._
