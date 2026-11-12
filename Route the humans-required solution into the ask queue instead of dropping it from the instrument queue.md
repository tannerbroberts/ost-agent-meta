---
type: Solution
source: 'agent-ideation:2026-08-30-unattended-sweep'
created: '2026-08-30'
evidence: assertion
killIf: >-
  Eight weeks after the route ships, no ask that arrived through it has been
  answered by anyone
killBy: '2026-12-31'
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[The operator answers an ask that arrives with a clock on it at a rate above zero]]

**Variation dimension: where-it-lives — which queue the item is reported in. Position taken: it moves, and nothing is hidden.**

Do not filter the item away. Re-file it. A Solution whose every test is in a lane compute may not run leaves `solutionsMissingInstruments` and appears in `outstandingAsks`, which this sweep already emits, already carries the pre-filled `ost-agent result` line for, and already ages by how long the ask has gone unanswered. The item keeps its visibility and changes its claim: from "you failed to write a command" to "a person owes an answer, and it has been open N days."

**Why this position and not another.** The sibling that filters says the listing was wrong; this one says the listing was in the wrong place. The information a reader actually needs here is not "does this have a command" but "who is this waiting on and for how long" — and there is already a queue that answers exactly that, with an ageing field the filter candidate throws away. This vault's `outstandingAsks` currently holds 59 entries of which 59 have no recorded age, so the ask queue's own weakness is that things arrive on it without a clock; routing gives these arrivals a start date.

**Cheapest form.** Where the lane check would go in `solutionsMissingInstruments`, emit into the pending-ask path (`src/ost/pending-asks.ts`) instead of dropping, tagged with the solution that owes it, so the ask reads as "this solution is blocked on a person" rather than as a bare test title.

**What it deliberately does not do.** It takes no view on whether the lane is right. A mislabelled test routes just as smoothly as a correctly labelled one — this candidate improves where the item is filed and not whether it deserved the label, which is the third sibling's whole subject.

**What it gives up, plainly.** It is the most expensive of the three to build and the only one that makes a queue longer. The ask list already stands at 59 unanswered, and this pours 68-ish more onto it; if the operator is not answering the 59, adding to the pile converts an unclearable instrument bucket into an unclearable ask bucket and this candidate has achieved nothing but a rename. That is a real risk and the test beneath it is aimed squarely at it. It also cannot age what has already happened: everything routed on day one gets today's date, so the ageing column starts by lying about how long these have actually been open.

**What would make this the wrong pick.** If the operator's answering rate is near zero, routing is ceremony and the filter sibling is strictly better. If the operator does answer asks but has never seen these because they were buried in the wrong queue, this is the only candidate that helps at all.

**Honest note on how this was ideated.** All three candidates under this opportunity were composed in one context by one author; this surface holds no grant to run independent parallel ideators. Discount their apparent distinctness accordingly.

Unvalidated. Agent-ideated 2026-08-30; a human to review.

## Standing finding — what nine follow-up notes established (consolidated 2026-11-10)

**For a firing that meets this node in `solutionsMissingInstruments`: the cheap check comes first.** Run `ost_read_repo` with `probe: true` on `src/eval/buildable.ts`. If it still reads **23,611 bytes** and this node is still in the bucket, nothing has moved and nothing below needs re-deriving. It read 23,611 on 2026-10-11, 10-31, 11-07, 11-09 and 11-10. Add a line here only if that changes.

**1. The bucket holds owed answers, not unwritten commands.**
- The shown page of 25 was classified in full on 2026-09-03 (9 bodies read, 16 judged by title): **zero instrumentable**. Six name a harness artefact that is not in this repository (the Monitor pair, the background-task output directory, the job-control wait, harness compaction, the auto-read guard). Eighteen rest on desirability or viability. One, "Append-only tool surface with no delete or shell tool", would take a false red: a spec asserting "no delete tool" fails today only because the delete was added on purpose.
- The unlabelled, uninstrumented tests were enumerated on 2026-09-01: **67**, of which 46 name a human act in the title, and 14 of the other 21 had been examined with none instrumentable. The remaining 7 were not examined as of that note. On 2026-10-19 the stock was still 67 and none was created after 2026-08, so it is fixed legacy.
- The 45 entries beyond the shown page have never been paged to from this surface.

**2. For lane-labelled tests the routing has already happened, so the candidate is de-duplication there.** Lane-labelled tests and `outstandingAsks` were the same count on 2026-09-01 (62 and 62) and again on 2026-10-19 (69). A solution whose only test is labelled sits in both queues at once. That was checked per file on this node and on "Group the queue by error signature at read time, and change nothing on disk", not on all 70. So "instead of" in this node's title overstates the move, and the "pours 68-ish more" cost applies only to the unlabelled 67. A more accurate title would be nearer "stop counting a labelled test twice". The body was not rewritten to say so, because narrowing what a candidate proposes is the operator's call.

**3. The cause is a missing branch, read in source on 2026-09-07.** `solutionsMissingInstruments` in `src/eval/buildable.ts` (20,070 bytes at the time, read in full) excludes four things: non-Solutions, `status === "deferred"`, shipped solutions that `trustsShippedStatus` accepts, and solutions with no tests. It reads no `lane`. In the same module `testsAwaitingVerification` does: `if (n.lane === CAUTIOUS_LANE) continue;`. The repair is one line in a function that already imports the predicate. A spec for it would be an added assertion in an existing `test/eval/` suite (`clearability.test.ts`, `permit-staleness.test.ts`, `vacuous-red.test.ts`), so it would fail on the assertion and not as `no-spec`. Which file is the right home was not judged; `clearability.test.ts` is 33KB and was not read.

**4. It has not landed, and that rests on behaviour.** The file grew to 23,611 bytes by 2026-10-11 and now truncates before the function, so the body has not been re-read since 2026-09-07. What shows the branch is still missing is that this node is still listed while its only test reads `lane: humans-required`.

**5. The bucket now grows only when a pass labels a human-owed test correctly at birth.** Counts on 2026-10-19: 523 tests, 387 with `instrument:`, 69 with `lane:`, 67 with neither. The bucket went 69 (2026-08-30), 72 (2026-10-19), 70 (2026-11-10).

**6. Nothing on the unattended surface can clear it.** `ost_flag_humans_required` is withheld there. The exits are the code repair, or a human's `ost-agent lane --set` per test. Granting the label call to the unattended surface is a third route; it is a permission decision and the operator's.

**7. What re-checking has cost.** Between 2026-10-28 and 10-31, four sessions tried to Grep `src/eval/buildable.ts` directly and were refused on repo permission, and a fifth tried to read `test/eval/lane-aware-instrument-bucket.test.ts`, which does not exist. Five consecutive firings up to 2026-11-10 re-read this body in full. Many nodes in the bucket carry an "examined and deliberately left without an instrument" note for the same reason: the bucket re-presents them every pass.

**What none of this touches.** This candidate's open question is whether the operator answers asks. The ask queue has gone from 59 to 69 entries, every one with no recorded age and none answered. The counts above say the items are correctly described as asks; they say nothing about whether routing would get any answered.

**Why this node has no instrument.** A command could assert the lane exclusion exists, but that measures the de-duplication repair and not the belief this candidate staked.

_Sources: this vault's own sweep responses, frontmatter greps, node bodies read through `ost_read_tree`, and `ost_read_repo` reads and probes of the product repository, across firings from 2026-08-30 to 2026-11-10. First-party structure; it grounds feasibility, not desirability. Nothing was executed, and no instrument, lane, rung or status was ever changed by these notes. `ost_check` is withheld on the unattended surface, so none of these writes was verified by the invariant checker._

## Definition of done — and it is not a command

"Count how many routed asks the operator answers in the four weeks after they arrive with an age on them"

No command: this one is humans-required on purpose. The bar is **at least 5 of the routed asks answered within 4 weeks**. An exit code can prove the entries moved queues; it cannot observe whether anybody answered them, and whether they get answered is the entire belief this candidate rests on. The half that decides the verdict is why an unanswered entry went unanswered — mis-filed, too expensive, or no longer interesting — and no artifact on disk carries that reason.

The test title is quoted rather than wikilinked on purpose: its one backlink belongs to its parent assumption.

## History
- 2026-11-10 body edited, dropping `## 2026-08-30 — a first-party count of what the bucket it proposes to re-file is actually made of`, `## 2026-09-01 (later firing) — "instead of" is the wrong word: for most of these the routing has already happened, into both queues at once`, `## 2026-09-01 (later firing) — the residue this node treats as an unknown quantity is now composed, and it supports the candidate on correctness`, `## 2026-09-03 — the census's own stated limit on the shown page is closed: 25 of 25, zero instrumentable`, `## 2026-09-07 — the missing lane check is confirmed in the code, and the repair is one line in a function that already imports the predicate`, `## 2026-10-11 — the one-line lane exclusion named on 2026-09-07 has not landed, 34 days on`, `## 2026-10-19 — since 2026-09-01 the bucket has grown only through tests labelled correctly`, `## 2026-10-31 — the repair still has not landed, and firings keep paying to re-check it`, `## 2026-11-07 — cheap check from the 2026-10-31 note: still not landed` — Nine dated follow-up sections (2026-08-30 to 2026-11-07) had grown this node to 31KB, and at least five consecutive unattended firings re-read all of it to re-derive one unchanged verdict; their own transcripts then came back as new evidence. Folded the nine into one standing finding that opens with the cheap check. The candidate's own prose and its Definition of done are reproduced verbatim; every distinct count and code finding is kept; git holds the prior text.

## 2026-11-11 — the "remaining 7 not examined" limit in point 1 is closed

Point 1 above leaves 7 of the 67 unlabelled, uninstrumented tests unexamined. This firing enumerated the 67 again with one multiline Grep over the vault (frontmatter `type: AssumptionTest` carrying neither `lane:` nor `instrument:`): still **67**. A second Grep narrowed that to the ones whose body holds no `## ` section at all, i.e. never annotated by any pass: **20**. All 20 name a person as the measurement in the title (a reader, an operator, a reviewer, an interviewee, a second person, a hand comparison). The other 47 each carry at least one appended section. Five of those were read in full this firing ("Do the shipped sweeps actually find a planted instance", "Test humans can promote while the agent is blocked from validating", "Sweep both vault histories for writes that landed as undefined or empty", "Does refusing a newline inside a wiki-link catch breaks nothing else catches", "Does a placeholder outcome get replaced, or does it become the tree's real root") and each already records why it cannot take a red instrument: four were run or built and would be green on arrival, one is three people watched.

So no unlabelled test is left that a pass has not looked at and that a title suggests the repository could answer. What clears this bucket is unchanged from point 6: the lane branch in `src/eval/buildable.ts` (probed today, still 23,611 bytes) or a human's `ost-agent lane --set` / `ost-agent result` per test.

**Limits.** "Annotated" was measured as "has a `## ` heading", not by reading all 47; a section could be about something other than instrumentability. The 20 were judged by title only. The 45 solutions beyond the shown page of `solutionsMissingInstruments` are still unpaged from this surface. Nothing was executed, and no instrument, lane, rung or status changed. Unverified by design (`ost_check` withheld).

## 2026-11-12 — the "45 beyond the shown page" limit is closed as to identity, and sampled as to content

Cheap check first: `src/eval/buildable.ts` probes at 23,611 bytes and this node is still listed, so points 1–7 stand.

**The unpaged 45 can be named without paging.** The shown page is alphabetical and ends at "Run the same evidence through both and publish the diff as the pitch". One multiline Grep over the vault for Solution files whose body nowhere contains a vitest command (pattern: frontmatter opening `type: Solution`, then a body with no occurrence of the word, anchored start to end of file) returns 86 files. Restricted to titles sorting after the shown page (initial S–W, plus the one lowercase "npm setup wizard…") it returns 47. One of those is `status: shipped` ("The uncovered statement printed next to what the test asked for"), leaving 46 against a reported 45 hidden. So the hidden page is, to within one, the S–W Solutions with no command in their body. The other 14 of the 86 sort before the page boundary and are not in the shown 25; they were not examined.

**Of the 46, nine already carry an examination note** (matched on "left without one", "it is not a command", "No command, on purpose"). **Five more were read in full this firing**, chosen because their titles sound mechanical:
- "The run's report leads with what it was refused, so a denied night cannot read as a quiet one" — its Definition of done is a two-week operator count, stated as humans-required.
- "The instrument-writing step declares repo sight required and skips itself rather than inventing paths" — a blind rating of ten instruments, bar 8 of 10, and its own body says not to build before that runs.
- "Staleness decay that surfaces nodes for refresh" — its test needs a human's blind stale list first (noted on the test 2026-08-29).
- "Supervisor heartbeat consumes run journals and alerts on error" — its test's rule shipped in v0.5.0, so a spec would be green on arrival (noted on the test 2026-08-05). What is owed is a recorded result.
- "Tag every write a session makes with its session id, so the next pass can diff an unfinished session directly from git history" — one assumption has no test at all (noted 2026-08-17: no data source).

None of the five can take a red instrument that is red about its own question. That is 14 of 46 with a verdict on record and 32 judged by nothing but their title.

**Limits.** The 86 is "no vitest command in the body", which is a proxy for bucket membership; it over-counts by at least the one shipped node and the off-by-one is unexplained. The 32 were not read. Nothing was executed, and no instrument, lane, rung or status changed. Unverified by design (`ost_check` withheld).

## 2026-11-12 (later firing) — six more of the hidden page read: 20 of 46 now carry a verdict, 26 are judged by title only

Cheap check first: `src/eval/buildable.ts` probes at 23,611 bytes and this node is still listed, so points 1–7 stand.

The S–W Grep from the section above was re-run with the frontmatter anchored (`type: Solution` on line 2, no vitest command anywhere in the file) and returns the same 46 files. Six that no pass had examined were read in full, chosen because their titles sound mechanical:

- "Surface a rolling friction trend across the last N firings, not per-run" — its one belief is whether operators would go and look at a trend unprompted. A person's habit.
- "The solution names its own riskiest assumption, and the gate checks that one was tested" — its belief is whether authors nominate honestly, and its own body says to test that before building the gate.
- "Trace-vs-narrative reconciler that files disagreements as friction" — its belief is how often narrative and trace disagree materially, measured by a hand diff of three past sessions.
- "Tool layer forbids the agent from setting validated" — already the product's behaviour (`validated` is not a value `ost_set_status` accepts), so a spec would be green on arrival. What is owed is a recorded result.
- "The builder files a structured disconfirmation that the loop carries into the tree beside the red" — its Definition of done already says no command: an operator judges the first five.
- "Up-rank or down-rank whole classes of opportunities in one recorded act" — its belief is whether class ranking matches how the founder triages.

None can take an instrument that is red about its own question. No instrument was set.

**Limits.** The 26 remaining were not read. "Green on arrival" for the validated guard is from the tool's own schema on this surface, not from a spec read in the repository. Nothing was executed, and no instrument, lane, rung or status changed. Unverified by design (`ost_check` withheld).
