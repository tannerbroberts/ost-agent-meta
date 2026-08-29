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

**What was observed, first-party, by this pass.** `ost_next_work` reported `65 solution(s) whose tests are prose only`, the largest actionable-looking figure in the response. This sweep sampled seven of them and read each node in full: "Adopt the platform's own job-control wait…", "An operator-set evidence window in ost.config.yaml…", "Maintain a running per-item task list…", "A human-edited manifest of loop-prescribed call sequences…", "Append-only tool surface with no delete or shell tool", "Remote push optional and off by default", and "Name the specific mechanisms a hand process structurally cannot have".

**All seven were already deliberate, and each said so on itself.** Not one was an oversight. The reasons vary and every one is sound — the deciding artefact lives in the harness rather than in this repository, so no spec under `test/` can reach it; the belief is behavioural and needs real people; the mechanism already ships and an instrument would pass on arrival, which measures nothing; the node's own premise is half-superseded and a human owes it an (a)/(b) decision before anything is instrumented. Three of the seven name the same blocker in the same words: the lane label that would take them off this list is set by `ost-agent lane --set`, and `ost_flag_humans_required` is withheld from the unattended surface.

**So the queue is a ratchet.** A pass reads the bucket, works out that an entry is deliberate, has no tool to record that verdict in a form the bucket reads, and the entry is listed again next time at the same size. Seven passes did this to "Append-only tool surface with no delete or shell tool" before consolidating their seven near-identical annotations into one. This pass spent seven node reads re-deriving what earlier passes had already written down.

**Why this is a need and not a preference.** The operator reads `65` as discovery debt and budgets compute against it. The count of entries an unattended firing can act on is, on this sample, zero — and the report gives no way to tell the two apart. That is the same defect the tree already records for the evidence queue, where well-behaved firings inflate the backlog; this is the instrument-side instance of it, and it is larger.

**Litmus test (more than one way to address this?):** Yes, and they are genuinely different. Let the unattended surface record a humans-required verdict itself, since that direction only ever removes work from compute's reach. Have the bucket read the prose already on the node, so a stated deliberate disposition suppresses the entry. Report the bucket split into actionable and deliberately-parked with both counts, changing nothing about what is stored. Age the entries, so one parked for seven passes stops being reported as news. Passes.

**Sample honesty, stated because it bounds the claim.** Seven of sixty-five, chosen for titles that sounded mechanically answerable — which biases *toward* finding actionable entries, and found none. It is not a census, and the share is what decides whether the fix is a report change or a genuine backlog. A census is cheap and nobody has run one.

**Evidence rung: `assertion`, and the demotion is itself worth recording.** This pass first declared `observed` and the ceiling refused it: the reads are real and first-party, but the node's provenance is an agent run rather than a recording, and no byline confers a measurement rung. The refusal was correct and is left visible here rather than worked around.

**For a human to review:** whether a sibling under this category already states this need. This pass could not search the tree cheaply enough to be sure and judged the finding worth recording over the duplicate risk; if a sibling exists, merge rather than annotate.

## The census this node asked for, run over the visible 25 (unattended firing, 2026-08-29)

This node closed with "A census is cheap and nobody has run one." One is now run, over the portion of the bucket a firing can actually see, and it does not overturn the sample — it widens it from 7 to 25 and finds the same thing.

**The bound first, because it decides how much the result is worth.** `ost_next_work` caps `solutionsMissingInstruments` at 25 of 65. **The other 40 are not reachable from this surface at all** — the cap is a display cap with no window, offset or cursor, so no firing can enumerate them without the operator setting one. This is therefore a census of 38% of the bucket, and it is the largest census this surface is capable of. The 40 hidden entries are the reason the parent question is still open, and reading them is a human's move.

**Method, and its weaker half.** Twelve entries now carry a recorded examination — the seven this node sampled, plus "Axioms elicited at the moment a derivation needs them" (a firing earlier today), "Scheduled ambient passes that page the operator only at hard gates" (2026-08-26), and three read in full this pass ("A highlight criteria note the founder edits…", "Monitor states its accepted command grammar up front…", "Borrow the axiom set from a named body of practice…"). The remaining thirteen were classified **from their titles and this pass's prior knowledge of the branches they sit in, not from a full read.** That half is the weaker half and is marked as such below; a title-based classification of a marketing candidate is safe, and one of a config candidate would not have been — which is why every config-shaped entry was read rather than inferred.

**Result: 25 of 25 are unactionable by an unattended firing, and they fall into four kinds.**

| Kind | Count | Why no instrument | Entries |
|---|---|---|---|
| Market and pricing — real people are the measurement | 11 | Willingness to pay, cohort recruitment, interviews, publishing, positioning. No exit code encodes demand. | Charge for the maintained tree…; Charge nothing for the tool…; Concierge design-partner cohort; Continuous story-based interview habit; Instrumented public trial with a willingness-to-pay probe; Offer to run one free tree for a stranger's product…; Publish where the operator is already asking…; Run both for two weeks…; Run the same evidence through both…; Ship it as something that grades a hand-built tree…; Name the specific mechanisms a hand process structurally cannot have |
| Harness-side artefact — outside this repository | 6 | The deciding artefact is Monitor, the task list, or the session's own write guard. No spec under `test/` can reach it. | A background task's own output directory…; Adopt the platform's own job-control wait…; Auto-read a file before the first write or edit…; Monitor accepts a vetted until-loop primitive…; Monitor states its accepted command grammar up front…; Maintain a running per-item task list… |
| Longitudinal or felt — one person, over time | 6 | Whether someone keeps a note current, amends a config more than once, or feels imported axioms are theirs. Wall-clock and a person, not a command. | A highlight criteria note the founder edits…; An operator-set evidence window in ost.config.yaml…; Axioms elicited at the moment a derivation needs them…; Borrow the axiom set from a named body of practice…; Scheduled ambient passes that page the operator only at hard gates; A human-edited manifest of loop-prescribed call sequences… |
| Already shipped — an instrument would pass on arrival | 2 | The mechanism exists, so the command could not be red, and a green-on-arrival instrument is refused by `verifyInstrument` for measuring nothing. | Append-only tool surface with no delete or shell tool; Remote push optional and off by default |

**What this changes about the node's own framing, and it sharpens rather than confirms.** This node argued the sample "biases *toward* finding actionable entries, and found none." The full visible set shows why the bias was weaker than claimed: nearly half the bucket is marketing and pricing candidates that no reader would ever have expected to carry a spec. The honest restatement is that `solutionsMissingInstruments` is not one queue with a low yield — it is at least four queues with different owners, and only the fourth kind is a defect at all. A count that adds a pricing experiment to a shipped mechanism to a harness limitation is not measuring discovery debt; it is measuring how many solutions exist.

**Which sibling this favours, stated as a reading and not a decision.** Four kinds with four owners is an argument for the reporting candidate over the verdict-recording one: a single humans-required label would collapse the market, longitudinal and harness kinds into one bucket and still say nothing about the two shipped entries, whereas the distinction that actually helps the operator is *who owns this* rather than *is a person involved*. That is not this pass's call — both siblings now sit beneath this node with their own tests, and the choice is the operator's.

**Not acted on.** No lane was set, no entry was disposed, and the count will read 65 again next firing. Three of the twelve examined entries were annotated this pass so they are not re-derived a third time; the thirteen title-classified ones were not annotated, because a note asserting a verdict this pass reached without reading the node would be the exact unaudited dismissal the ledger's docstring warns about.

_First-party to this firing: the classification is this pass's own reading of the response and of five node bodies. Observed behaviour of the tool surface; grounds usability, not demand. No test was run, no result recorded, and this node's rung is unchanged._

## The census at 100%, and the bound that said it was impossible (unattended firing, 2026-08-29)

The section above closed with a bound: `ost_next_work` caps `solutionsMissingInstruments` at 25 of 65, so **"the other 40 are not reachable from this surface at all"** and "reading them is a human's move." **That bound is false, and this pass measured the whole set.** It is worth correcting precisely because it was stated as a property of the surface rather than of the tool — the cap is real, but the cap is not the only way to reach the data.

**The method, so it can be checked or disputed.** The vault's node files are on disk and this surface has ordinary filesystem read. Three greps over `*.md` frontmatter and one sequential diff:

- `^type: AssumptionTest` — **477** files.
- `^instrument:` — **355** files.
- `^lane: humans-required` — **54** files.

Both file lists come back in the same order, so the second is a subsequence of the first and the diff is mechanical rather than judged. It resolves exactly: 477 − 355 = **122** tests carry no instrument, and 54 + 68 = 122. No tool cap applies, because no tool was asked.

**The result: the bucket is two populations, and one of them is already labelled.**

| | Count | What it is |
|---|---|---|
| Tests with an instrument | 355 | Finished, whatever their verdict |
| No instrument, `lane: humans-required` | **54** | Already labelled. A person is already named as the measurement |
| No instrument, no lane | **68** | The genuinely unlabelled set |
| Total tests | 477 | |

**The defect this exposes, verified rather than inferred.** The 54 lane-labelled tests **still populate `solutionsMissingInstruments`**. Checked end-to-end on two entries from the visible 25, following Solution → Assumption → AssumptionTest in full:

- "A human-edited manifest of loop-prescribed call sequences the harvester suppresses" → "The founder will keep a manifest of prescribed call sequences current as the loop's steps change" → "Count how many recurring-input artifacts the founder has actually kept current, before asking for another" — `lane: humans-required`.
- "An operator-set evidence window in ost.config.yaml, amended by hand like discovery.target" → "An operator who must move the window by hand will actually move it more than once" → "Count how many times the operator amends discovery.target over eight weeks of git history" — `lane: humans-required`.

Two of two. Each solution has exactly one assumption carrying exactly one test, and that test is already labelled. **So the label that exists specifically to take work off compute's reach does not take it off this bucket.** That is not a reporting preference — it is the same fact counted twice, and it is why a pass can read an entry, find it deliberate, label it correctly, and still be handed it again. The evidence channel has already recorded the cost of the loop rediscovering this: `TRANSCRIPT:14f184b4-6ca1-41d3-bf1f-b9e036b2a1a0` holds three consecutive `ost_set_instrument` refusals on one humans-required test, two of them bad-instrument attempts before the lane refusal landed.

**The 68 unlabelled, sampled five and read in full. None was instrumentable, and they split two ways.**

*Already answered — an instrument would be green on arrival and is correctly refusable:*

- "Sweep both vault histories for writes that landed as undefined or empty" — run 2026-07-27, 306 entries classified, threshold not crossed, consequence shipped in v0.18.0 as a tripwire.
- "Do the shipped sweeps actually find a planted instance" — run 2026-07-27, 12 plants, 12 found, and it **left a permanent spec behind**: `test/eval/planted-instance.test.ts`, shipped v0.20.0.
- "Test can a full pass be done with no delete or edit tool" — settled by events against its own threshold once `ost_edit_node` / `ost_merge_nodes` / `ost_detach_nodes` shipped. Its own 2026-08-05 note already says a spec written now "could not go red honestly."

*Genuinely humans-required and merely unlabelled — a person is the measurement and no lane says so:*

- "Backdated half-life comparison for staleness flags" — the test requires a human to mark a stale list by hand **before** seeing any setting's output.
- "Judge the eighteen reopened items — were they genuinely finished" — its own body says why: "Asking compute to grade it would be asking the disputed rule to referee its own dispute."

**What this changes about the parent question.** The node above concluded the bucket is "at least four queues with different owners." The census sharpens that in the direction that matters for a fix: the largest single correction available is not a new mechanism but **subtracting work that is already dispositioned** — 54 entries carry the label today and are reported anyway. A split that honoured the existing lane field would shrink the reported figure without anybody judging anything, and the sibling "The split reports defaulted-parked apart from labelled-parked, rather than folding both into one number" already carries an instrument for exactly that distinction.

**The concrete move for the operator, because it is small and this surface cannot make it.** `ost_flag_humans_required` is withheld here, so the two unlabelled tests named above need `ost-agent lane --set`. That is two commands, and it moves two entries from the unlabelled 68 into the already-labelled 54 where they belong.

**What this does not settle, stated so it is not over-read.** The 68 were classified by reading **five** of them, chosen for sounding mechanically answerable — the same bias the earlier sample declared, and it again found nothing instrumentable. The other 63 are classified by nothing and are not classified here. The 122/54/68 split is a count of frontmatter fields and is exact; the *kinds* underneath the 68 are a five-record sample and are not. No test was run, no result recorded, no lane set, and no rung moved.

_First-party to this firing: three greps over the vault's own files, one sequential diff, and seven node bodies read in full. Observed behaviour of files on disk. `ost_check` is withheld on this surface, so these writes are unverified by the invariant checker by design._

## The unlabelled 68, sampled eight more — and one of them was instrumentable (unattended firing, 2026-08-29, second firing)

The section above closed by naming its own weakest part: the 68 unlabelled tests were "classified by reading **five** of them… The other 63 are classified by nothing." This pass read eight more, chosen the same way — titles that sounded mechanically answerable — and the result **does not reproduce the earlier finding**. One of the eight was genuinely instrumentable, and it has been instrumented.

**The eight, with the field check that qualifies each as a member of the 68** (no `instrument:`, no `lane:` in frontmatter, verified per file rather than inferred from a diff):

| Test | Kind | Why |
|---|---|---|
| Does the guard catch real laundering without refusing honest commands | **Instrumentable** | Prose already declares `Lane: compute-only` and names `runs.jsonl` as the artefact. Two numeric edges, both counts over a corpus on disk. **Instrumented this pass.** |
| Does refusing a newline inside a wiki-link catch breaks nothing else catches | Already answered | Declares `Lane: compute-only`; the run is recorded in the body against all three pre-committed bars and cleared every one. The verdict was never filed, because `ost-agent result` is human-only. |
| Backdated half-life comparison for staleness flags | Humans-required, unlabelled | A human hand-marks the stale set first; that list is the reference every setting is scored against. |
| Check what would actually have to be redacted before a vault could live in a shared repo | Humans-required, unlabelled | Its own body: "have a person mark every node" and "A human runs this and records the result." |
| Rewrite the shortest helper against the bundled runtime and compare length and readability | Humans-required, unlabelled | Half the threshold is "the reader says they would still edit it." |
| Count how much post-handoff work in past sessions would have survived a failing check | Humans-required, unlabelled | Its own body: "Proposed by the agent; a human runs it and records the outcome." |
| Group the harvested tool errors by hand and see whether one rule reproduces the grouping | Humans-required, unlabelled | Hybrid — the rule is computable, but only against a hand grouping that does not exist yet. |
| Hand-label the gated rows and check whether a detector agrees | Humans-required, unlabelled | Same hybrid shape: the hand labelling is the reference the detector is scored against. |

**What changes, and it is the headline.** The earlier sample found 0 of 5 instrumentable and concluded the 68 split two ways — already-answered or genuinely humans-required. At 13 of 68 examined the split is **three** ways, and the third kind is not empty: a test whose own prose declares compute-only, names the artefact, and carries a bound threshold, sitting unlabelled and uninstrumented since 2026-07-27. That is a real backlog item, not a reporting artefact. One in thirteen is a low yield and it is not zero, and the difference between those two matters here because "the bucket is entirely unactionable" was becoming the settled reading.

**The largest kind is still the one the earlier pass named.** Six of eight are humans-required and merely unlabelled — the same class as the two the section above sent to `ost-agent lane --set`. That list is now eight. Each one is a `lane --set` away from moving out of the unlabelled 68 into the already-labelled 54, and none of them can be moved from this surface.

**A methodological correction to the section above, because it bears on how much its membership claim is worth.** That section derived the 68 by a sequential diff, justified as: "Both file lists come back in the same order, so the second is a subsequence of the first and the diff is mechanical rather than judged." **The orderings are not consistent between the two greps.** Checked on this pass's own output: in the instrument-grep the entry at position 240 corresponds to position 434 of the AssumptionTest list, while the entry at position 354 corresponds to position 240 of it — the mapping runs backwards across that span, so it is not a subsequence and a positional diff over it is not sound. Two things follow, and they point in opposite directions. The **counts** are unaffected — 477, ~355 and 54 are counts of frontmatter fields and each is exact on its own. The **membership** of the 68, if it was ever enumerated positionally, is not established. This pass therefore verified each of its eight per file, which is slower and is the only method that holds. (One smaller discrepancy alongside it: `^instrument: npx` matches 354 files against that section's 355 for `^instrument:`, consistent with a single test carrying an instrument value that is folded or not npx-prefixed.)

**Bound on this pass, stated plainly.** Thirteen of sixty-eight are now examined; fifty-five are not. The sampling is still biased toward titles that sound mechanically answerable, which is the bias that should *over*-find instrumentable entries — and it found one in eight, which puts a low ceiling on what a full census would return but not a zero one. This pass also **did not read the product repository**: `ost_read_repo` is withheld from the unattended path and a filesystem listing of the checkout was refused, so every judgement above is from node bodies and frontmatter on disk. No lane was set, no result recorded, and the reported figure will read 65 again next firing.

_First-party to this firing: eight node bodies read in full, three more read and found already instrumented, and its own two greps. Observed behaviour of files on disk; it grounds usability, not demand. `ost_check` is withheld here, so these writes are unverified by the invariant checker by design._
