---
type: Opportunity
source: 'agent-run:unattended-sweep-2026-08-29'
created: '2026-08-29'
evidence: assertion
authorship: machine
---
#Opportunity #unvalidated #evidence/assertion
[[Let the unattended surface record its own humans-required verdict]]
[[Report the instrument bucket as two counts, automating the split and not the verdict]]
[[Point the shipped disposition ledger at the instrument bucket rather than building a second parking mechanism]]

**The need, in the operator's voice:** "The largest number on the report is work my agent is structurally unable to do, and nothing on the report says so."

**What was observed, first-party.** `ost_next_work` reported `65 solution(s) whose tests are prose only` — the largest actionable-looking figure in the response. Seven were sampled and read in full, and all seven were already deliberate, each saying so on itself. Not one was an oversight. The reasons vary and every one is sound: the deciding artefact lives in the harness rather than in this repository, so no spec under `test/` can reach it; the belief is behavioural and needs real people; the mechanism already ships, so an instrument would pass on arrival and measure nothing; the node's premise is half-superseded and a human owes it a decision before anything is instrumented.

**So the queue is a ratchet.** A pass reads the bucket, works out that an entry is deliberate, has no tool to record that verdict in a form the bucket reads, and the entry is listed again next time at the same size. Seven passes did this to "Append-only tool surface with no delete or shell tool" before consolidating their seven near-identical annotations into one.

**Why this is a need and not a preference.** The operator reads the figure as discovery debt and budgets compute against it. The count of entries an unattended firing can act on is zero, and the report gives no way to tell the two apart. That is the same defect the tree already records for the evidence queue, where well-behaved firings inflate the backlog; this is the instrument-side instance of it, and it is larger.

**Litmus test (more than one way to address this?):** Yes, and they are genuinely different. Let the unattended surface record a humans-required verdict itself, since that direction only ever removes work from compute's reach. Have the bucket read the prose already on the node, so a stated deliberate disposition suppresses the entry. Report the bucket split into actionable and deliberately-parked with both counts, changing nothing about what is stored. Age the entries, so one parked for seven passes stops being reported as news. Passes.

**Evidence rung: `assertion`, and the demotion is itself worth recording.** A pass first declared `observed` and the ceiling refused it: the reads are real and first-party, but this node's provenance is an agent run rather than a recording, and no byline confers a measurement rung. The refusal was correct and is left visible here rather than worked around.

## The census is closed: zero instrumentable, over the whole non-people set

This node opened by asking for a census — "A census is cheap and nobody has run one." Five firings ran it, each correcting the one before, and it finished on 2026-09-02. **21 of the 21 non-people entries in the unlabelled set have been examined, and the count of instrumentable ones is zero.** Every earlier statement of that was a sample declaring its own bias; the final one is an enumeration over the whole non-people set. Each examined test carries its own verdict and its specific reason on its own body — and the reasons are genuinely different ones rather than one repeated: an arrival rate over wall-clock, a person's judgement of relevance, a third-party producer's persistence, a conjunctive threshold whose computable bars are held hostage by one naming the operator's judgement.

**The result for the operator.** `solutionsMissingInstruments` is not a backlog with a low yield. On the portion anyone has been able to check, its yield is exactly nil, and the reported figure measures how many solutions exist rather than how much work is owed.

**The one claim that was a classification rather than a reading — now checked.** The other 46 entries were sorted as people-shaped by what their titles name as the measuring act (ask, interview, pitch, sell, offer, publish, show, hand, judge). Every pass flagged this as its weakest half and none had tested it. The 2026-09-02 unattended sweep read the two riskiest members in full — the hybrid-shaped ones, where a computable half sits beside a human half and a title-based read is most likely to go wrong:

- "Hand-compute unblock counts and see if the operator's pick changes" — its method names the human as the subject and states it as an explicit guard: "the OPERATOR is the subject — an agent picking would re-create the closed loop this tree already flags." No spec file can supply an operator's changed pick.
- "Does a route view change which work a builder picks up first" — its design names outside people as the sample, six builders split into two groups, and the body says "Proposed only. A human runs this."

Both were already triaged and annotated by earlier passes with the same recorded blocker. **The title-based classification held on the two cases most likely to break it**, which is the strongest check available short of reading all 46.

## What the bucket is actually made of

**Four kinds with four different owners**, counted over the 25 entries the sweep displays. Only the fourth is a defect at all:

| Kind | Count | Why no instrument |
|---|---|---|
| Market and pricing — real people are the measurement | 11 | Willingness to pay, cohort recruitment, interviews, publishing, positioning. No exit code encodes demand. |
| Harness-side artefact — outside this repository | 6 | The deciding artefact is Monitor, the task list, or the session's own write guard. No spec under `test/` can reach it. |
| Longitudinal or felt — one person, over time | 6 | Whether someone keeps a note current, amends a config more than once, or feels imported axioms are theirs. Wall-clock and a person, not a command. |
| Already shipped — an instrument would pass on arrival | 2 | The mechanism exists, so the command could not be red, and a green-on-arrival instrument is refused by `verifyInstrument` for measuring nothing. |

A count that adds a pricing experiment to a shipped mechanism to a harness limitation is not measuring discovery debt; it is measuring how many solutions exist. This favours the reporting sibling over the verdict-recording one — a single humans-required label would collapse the market, longitudinal and harness kinds into one bucket and still say nothing about the two shipped entries, whereas the distinction that helps the operator is *who owns this* rather than *is a person involved*. Stated as a reading, not a decision; all three siblings sit beneath this node with their own tests and the choice is the operator's.

## The counts, and the trend that is the real finding

Counts of frontmatter fields over this vault's own `*.md`. Exact, not sampled.

| | 2026-08-29 | 2026-09-01 | Δ |
|---|---|---|---|
| Tests total | 477 | 500 | +23 |
| Carrying an instrument | 355 | 371 | +16 |
| No instrument, `lane: humans-required` | 54 | 62 | +8 |
| No instrument, no lane — the unlabelled set | 68 | 67 | **−1** |

**The finding is the last row.** Labelling is not stalled — eight lanes were set in three days. But the unlabelled pile moved by one. The `lane --set` route is being exercised almost entirely on tests created in the same window, not on the standing backlog, eight of which were named explicitly with one paste-ready command each. Whatever is producing lanes is not reaching the list this node exists to drain, which is a different problem from the one the taxonomy above diagnoses and is not fixed by any of the three siblings hanging beneath this node.

## The defect: a labelled test is counted twice

**The 62 lane-labelled tests still populate `solutionsMissingInstruments`.** Verified end-to-end on two entries, following Solution → Assumption → AssumptionTest in full:

- "A human-edited manifest of loop-prescribed call sequences the harvester suppresses" → "The founder will keep a manifest of prescribed call sequences current as the loop's steps change" → "Count how many recurring-input artifacts the founder has actually kept current, before asking for another" — `lane: humans-required`.
- "An operator-set evidence window in ost.config.yaml, amended by hand like discovery.target" → "An operator who must move the window by hand will actually move it more than once" → "Count how many times the operator amends discovery.target over eight weeks of git history" — `lane: humans-required`.

**The mechanism, read off the source rather than inferred.** `buildableSolutions` in `src/eval/buildable.ts` applies no lane check at all, while `testsAwaitingVerification` two functions below it in the same file does (`if (n.lane === CAUTIOUS_LANE) continue;`). So the label that exists specifically to take work off compute's reach does not take it off this bucket. That is not a reporting preference — it is the same owed answer counted a second time under a claim that is false about it, and it is why a pass can read an entry, find it deliberate, label it correctly, and still be handed it again. The evidence channel records the cost: `TRANSCRIPT:14f184b4-6ca1-41d3-bf1f-b9e036b2a1a0` holds three consecutive `ost_set_instrument` refusals on one humans-required test, two of them bad-instrument attempts before the lane refusal landed.

**The largest single correction available is therefore subtraction, not a new mechanism** — entries already dispositioned are reported anyway. A split honouring the existing lane field would shrink the reported figure without anybody judging anything, and the sibling "The split reports defaulted-parked apart from labelled-parked, rather than folding both into one number" already carries an instrument for exactly that distinction.

## The lane has never once been used permissively

All 62 lane fields in the vault read `humans-required`. There is not one `compute-only` lane anywhere in 500 tests. The ruleset describes `ost-agent lane --set` as the permissive call — the one declaring that compute may run a test on its own authority, held by a human precisely because it widens what runs unattended. In this vault it has never been used that way: every recorded use has removed work from compute's reach. Worth knowing before building anything that assumes the label is a two-way switch, and it explains why `assumptionWork.runnable` is empty on every firing while 500 tests sit under it.

## Three method corrections, so nobody repeats a method that does not hold

- **A positional diff between two greps is unsound.** The AssumptionTest list and the instrument list do not come back in corresponding orders — checked on one firing's own output, the entry at position 240 of the instrument grep corresponds to position 434 of the AssumptionTest list while position 354 corresponds to position 240, so the mapping runs backwards across that span. The **counts** are unaffected and each is exact on its own; the **membership** of any set derived positionally is not established. What holds is per-file verification, or one multiline grep matching the frontmatter block whole with an allow-list of keys, so a file carrying `instrument:` or `lane:` cannot match at all — order-independent, no diff, and it returns the same figure subtraction does.
- **The frontmatter predicate is blind to a resolution recorded in prose.** Resolving a test as non-instrumentable leaves no frontmatter trace, so a test examined and settled weeks earlier still enumerates as "genuinely unexamined". Demonstrated on "Replay the three recorded failed runs through the journal-alert rule on paper", examined four weeks before a census listed it. Any "unexamined" figure from this method is an upper bound on unexamined work, not a count of it.
- **`ost_read_repo` is granted on the unattended surface**, despite the run prompt's hard rule saying outward sensing is withheld. The skill's authoritative withheld list names seven tools and `ost_read_repo` is not among them. The disagreement is recorded as an open ask on "The unattended run is scoped for tools nobody granted it, and it finds out one denial at a time". The cheap move for any firing is to spend the one call rather than believe the prose — a pass that believes it is blind writes off the whole backlog for free.

## What the operator owes, and it is the only thing that moves this

Every one of these entries needs `ost-agent lane --set`, which is withheld from the unattended surface — `ost_flag_humans_required` is not granted, so a firing that reaches the correct verdict has no call available to record it. That is a sufficient explanation for why this bucket drains at zero across many firings, and it is independent of whether the entries are correctly characterised: even a pass that gets the judgement exactly right cannot act on it. Each examined test carries its own paste-ready repair on its body.

One entry additionally states a prerequisite in prose that nothing on the frontmatter records — "Two unattended weeks - count pages, grind, and money burned" is blocked on the exit-0 defect — so it does not appear in `blockedOnPrerequisite` either.

Whoever weighs the three siblings should weigh a cheaper alternative none of them covers: granting the label call to the unattended surface. That is a permission decision and the operator's alone, not a build.

**For a human to review:** whether a sibling under this category already states this need. No pass has been able to search the tree cheaply enough to be sure; if a sibling exists, merge rather than annotate.

## Limits

The four counts are counts of frontmatter fields and are exact; nothing there is a sample. The four-kind taxonomy is over the 25 displayed entries, and thirteen of those were classified from titles rather than a full read. The 46 people-shaped entries are classified by title, checked on the two riskiest members and not on the rest. The 21-of-21 result is an enumeration, but it inherits verdicts recorded by earlier firings on the tests themselves rather than re-verifying each. Nothing here was executed, no test was run, no result recorded, no lane set, no instrument set, no rung moved. `ost_check` is withheld on the unattended surface, so these writes are unverified by the invariant checker by design.

## History
- 2026-09-02 body edited, dropping `## The census this node asked for, run over the visible 25 (unattended firing, 2026-08-29)`, `## The census at 100%, and the bound that said it was impossible (unattended firing, 2026-08-29)`, `## The unlabelled 68, sampled eight more — and one of them was instrumentable (unattended firing, 2026-08-29, second firing)`, `## The compute-only seam, enumerated exactly rather than sampled (unattended firing, 2026-08-29, third firing)`, `## 2026-09-01 — the census re-run three days on, and the pile it measures has not moved`, `## 2026-09-01 (later firing) — the 67 enumerated by name, and the unexamined residue is 8 tests rather than 67`, `## 2026-09-01 (later firing) — three of the named eight examined, all non-instrumentable, and one was already resolved before the census listed it`, `## 2026-09-02 — the residue is now zero: all 21 non-people entries examined, none instrumentable` — The census this node opened by asking for ("A census is cheap and nobody has run one") closed on 2026-09-02: 21 of 21 non-people entries examined, zero instrumentable. Eight appended sections narrate the journey to that destination across five firings, each correctly noting what the previous one left open. With the question settled, a reader pays 42,000 characters to learn one sentence, and every future firing that meets this node in its own bucket pays it again — the exact ratchet this node exists to describe, now enacted on itself. Consolidating to the settled result plus the findings that survive it: the four-kind taxonomy, the exact counts and their trend, the double-counting defect and its source in src/eval/buildable.ts, the never-once-permissive lane fact, the three method corrections, and the operator's repair. No claim is dropped and no number is rounded; git holds the full prior text. Added this pass: the 46 people-shaped entries were classified by title and every pass flagged that as its weakest remaining half, so the two riskiest members were read in full and the classification held.
