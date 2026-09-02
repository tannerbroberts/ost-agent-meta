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

## The compute-only seam, enumerated exactly rather than sampled (unattended firing, 2026-08-29, third firing)

The section above closed on its own weakest point: thirteen of sixty-eight examined, "fifty-five are not", and the sampling biased toward titles that sound answerable. Sampling further would have added another eight-of-sixty-eight anecdote. This pass instead **enumerated the one seam where an instrumentable entry could still be hiding, and found it empty**. No sampling, no titles, no judgement about what sounds mechanical.

**The seam, and why it is the right one to close first.** The single strongest predictor that a test can carry a command is that the test *says so itself*. The one instrumentable entry the previous firing found — "Does the guard catch real laundering without refusing honest commands" — was found exactly that way: its prose already declared compute-only. So the question worth answering exactly is: how many tests declare compute-only in prose and still carry no instrument?

**Method, name-based and reproducible.** Two greps over the vault's own `*.md`, matched on filename rather than on position — the previous section established that positional diffing between these two lists is unsound because the orderings do not correspond, and it is right, so nothing here relies on order.

- prose declaring compute-only (`^\*\*Lane: compute-only`) — **97** files.
- carrying an instrument (`^instrument:`) — **356** files.

**Result: 93 of the 97 already carry an instrument. Four do not, and all four are accounted for.**

| Test | State |
|---|---|
| Sweep both vault histories for writes that landed as undefined or empty | Already answered — run 2026-07-27, examined by an earlier firing today |
| Do the shipped sweeps actually find a planted instance | Already answered — run 2026-07-27, left `test/eval/planted-instance.test.ts` behind |
| Does refusing a newline inside a wiki-link catch breaks nothing else catches | Already answered — run, cleared all three bars, verdict never filed |
| Do named unfixed thresholds actually get fixed | **Newly examined this pass.** Annotated on itself |

**The fourth was never examined before and is not what it looks like.** Its prose reads "Lane: compute-only for the census, humans-required for the fixing" — two lanes in one node, the exact construction the ruleset names by example as forbidden. And the compute half it reserves is not outstanding work: `test/eval/unfixed-thresholds.test.ts` exists and passes, exercising `thresholdKindOf`, `askedOf` and `computeUnfixedThresholds` over all four threshold classifications, with the same 21-of-27 census this vault records stated in its own header. So an instrument there would be green on arrival. What survives is the desirability question alone, and the repair is one `ost-agent lane --set` naming the whole test humans-required. That command is written out on the node.

**What this settles, stated no wider than it goes.** The highest-yield seam in the unlabelled 68 is now closed by enumeration rather than estimated by sample: **zero instrumentable entries remain among tests that declare compute-only.** That does not say the 68 hold nothing — a test could be compute-answerable without saying so, and those are untouched by this method. It does mean the cheap search is finished, and any further yield has to come from reading nodes that give no signal in their own prose, which is a much worse trade than the one-in-eight the previous section measured.

**Correcting a bound this node has carried all day, because it changed what three firings did.** Both sections above state that the pass could not read the product repository — "`ost_read_repo` is withheld from the unattended path". **On this firing it is granted and it answers**, and the repo reads above are what turned the fourth test from a title into a resolved item. The skill's own authoritative withheld list names seven tools and `ost_read_repo` is not among them; the run prompt's hard rule says outward sensing is withheld. The two disagree, the disagreement is already recorded as an open ask on "The unattended run is scoped for tools nobody granted it, and it finds out one denial at a time", and the cheap move for any future firing is to spend the one call rather than believe the prose. A pass that believes it is blind writes off the whole backlog for free.

_First-party to this firing: two greps over the vault's files, one name-based set difference, four node bodies and two repository files read in full. Observed behaviour of files on disk; it grounds usability, not demand. No test was run, no result recorded, no lane set, no rung moved. `ost_check` is withheld here, so these writes are unverified by the invariant checker by design._

## 2026-09-01 — the census re-run three days on, and the pile it measures has not moved

Kept short, per the convention the sections above follow. This is the same enumeration the 2026-08-29 firings ran, repeated after three days, and only the differences are below.

**The counts, by the same name-based method** (greps over this vault's own `*.md` frontmatter; verified test-scoped this pass by confirming that no node of type Solution, Opportunity or Assumption carries an `instrument:` or `lane:` field, so every match is an AssumptionTest):

| | 2026-08-29 | 2026-09-01 | Δ |
|---|---|---|---|
| Tests total | 477 | **500** | +23 |
| Carrying an instrument | 355 | **371** | +16 |
| No instrument, `lane: humans-required` | 54 | **62** | +8 |
| No instrument, no lane — the unlabelled set | 68 | **67** | **−1** |

**The finding is the last row, and it is a trend rather than a count.** Labelling is not stalled — eight lanes were set in three days. But the unlabelled pile moved by one. So the `lane --set` route is being exercised almost entirely on tests created in the same window, not on the standing backlog those sections identified and wrote paste-ready commands for. Eight of that backlog were named explicitly across the 2026-08-29 sections as one command each; three days later the population is 67. Whatever is producing lanes is not reaching the list this node exists to drain, which is a different problem from the one the sections above diagnose and is not fixed by any of the three siblings hanging beneath this node.

**One fact no section here states, and it cuts at the framing.** All 62 lane fields in the vault read `humans-required`. There is not one `compute-only` lane anywhere in 500 tests. The ruleset describes `ost-agent lane --set` as the permissive call — the one that declares compute may run a test on its own authority, held by a human precisely because it widens what runs unattended. In this vault it has never once been used that way: every recorded use has removed work from compute's reach. That is worth knowing before building anything that assumes the label is a two-way switch, and it explains why `assumptionWork.runnable` is empty on every firing while 500 tests sit under it.

**The cheap seam is still closed, checked a second way.** Rather than re-run the compute-only prose grep, this pass enumerated tests carrying no threshold, no instrument and no lane — the worst-off state available — and found exactly six. Four are the already-answered compute-only set the 2026-08-29 third firing closed on ("Sweep both vault histories for writes that landed as undefined or empty", "Do the shipped sweeps actually find a planted instance", "Does refusing a newline inside a wiki-link catch breaks nothing else catches", "Do named unfixed thresholds actually get fixed"). The other two are "Test humans can promote while the agent is blocked from validating" and "Backdated half-life comparison for staleness flags", both already annotated as humans-required with the mechanical half discharged. **Zero new instrumentable entries.** A different method reaching the same empty result three days later is worth more than the first result alone.

**Limits.** The four counts are counts of frontmatter fields and are exact; nothing here is a sample. The Δ column compares against figures recorded on this node by another firing and inherits whatever those got wrong — in particular that section itself flags a 355/354 discrepancy on the instrument grep. Membership of the 67 was not enumerated, only its size, and the six named above were verified per file rather than by diff, per the correction the section above establishes. This says nothing about whether the 67 contain a compute-answerable test that does not say so in its prose, which remains the untouched residue.

_First-party to this firing: five greps over this vault's files and thirteen node bodies read in full. Observed behaviour of files on disk; it grounds usability, not demand. No test was run, no result recorded, no lane set, no rung moved. `ost_check` is withheld on this surface, so this write is unverified by the invariant checker by design._

## 2026-09-01 (later firing) — the 67 enumerated by name, and the unexamined residue is 8 tests rather than 67

Kept short, per this node's convention. The section above closes on exactly one open item — "Membership of the 67 was not enumerated, only its size… This says nothing about whether the 67 contain a compute-answerable test that does not say so in its prose, which remains the untouched residue." This pass enumerated the membership and narrowed that residue.

**The method, which is the part worth reusing.** Earlier sections establish that a positional diff between the AssumptionTest list and the instrument list is unsound (the orderings do not correspond) and that per-file verification is the only method that holds but is slow. There is a third: match the frontmatter block whole, with an allow-list of keys, so a file carrying `instrument:` or `lane:` cannot match at all. One multiline grep, order-independent, no diff and no per-file pass. It returns **exactly 67** — the same figure the section above reached by subtraction, now with names attached.

**Result over the full population, not a sample.** Classifying all 67 by what the title names as the measuring act:

| | Count | Basis |
|---|---|---|
| People-shaped on their face | **46** | The title names the human act — ask, interview, pitch, sell, offer, publish, show, hand, judge, "would operators" |
| Not obviously people-shaped | **21** | Everything else |
| — of those, already examined and resolved | **12** | Recorded on this node or on the test itself: already-answered, or humans-required in substance |
| — of those, genuinely unexamined | **9** | Named below |

**The residue, named so nobody re-derives it.** "Apply the escalating message to the five-failure session and check where it would have fired" (its node is `deferred`, so it is retired and the live residue is **8**); "Does a placeholder outcome get replaced, or does it become the tree's real root"; "Replay the three recorded failed runs through the journal-alert rule on paper"; "Settle the known prompts as config and count how many new ones appear in a month"; "Give a cold session only the tree and see whether it can say why the work exists"; "Follow a candidate source list for a month and count items that bear on anything open"; "Set up one scheduled export and check every week whether it is still arriving"; "Count how many of the operator's real experiment sources can push anywhere at all"; "Two unattended weeks - count pages, grind, and money burned".

**And four of those eight are longitudinal on their face** — a month, every week, two weeks, "on paper". So the plausible instrumentable yield left in the 67 is smaller than eight, and the cheap search this node declared closed on 2026-08-29 is now closed by enumeration over the whole set rather than by seam.

**Two examined this pass, both resolved humans-required.** "Install the package on ten stock setups and see whether postinstall ever gets to speak" — needs publish rights and ten real environments; its own body says "A human, or an attended session with publish rights" and names the release-credential dependency. "Replay ten past runs and count how many needed a scope nobody would have predicted" — the measurement is a person judging what they would have granted knowing only the task, and its own limits paragraph asks for a second person to debias it. Neither can take an exit code. That makes it 14 of 21 non-people entries examined across all passes, and still **zero instrumentable**.

**Limits.** The 46/21 split is classification by title, not by body, and it is the weaker half — a title-based read of a marketing candidate is safe and one of an ambiguous candidate is not, which is why the 21 are treated as unresolved rather than dismissed. The 12 already-examined rest on notes recorded by earlier firings on the tests themselves, inherited rather than re-verified here. The enumeration is exact and reproducible; the kinds underneath it are not. Nothing was executed, no lane set, no instrument set, no rung moved, no status changed, and no node created.

_Method: one multiline frontmatter grep over this vault's `*.md`, plus six node bodies and two test bodies read in full, and a first-party `ost_read_repo` read of `src/eval/buildable.ts`. Observed structure of files on disk; it grounds usability, not demand. `ost_check` is withheld on this surface, so this write is unverified by the invariant checker by design._

## 2026-09-01 (later firing) — three of the named eight examined, all non-instrumentable, and one was already resolved before the census listed it

Kept short, per this node's convention. The section above closes by naming the residue "so nobody re-derives it" and leaves eight tests unexamined. This firing examined three of the eight and found the residue is smaller than eight for a reason the enumeration method cannot see.

**What was read, first-party.** Three of the named eight, in full, from disk: "Replay the three recorded failed runs through the journal-alert rule on paper", "Does a placeholder outcome get replaced, or does it become the tree's real root", and "Count how many of the operator's real experiment sources can push anywhere at all". Denominator stated first: three of eight, chosen as the three whose titles were least obviously longitudinal, so the sample is biased *towards* finding an instrumentable one.

**Result: zero instrumentable, and the three fail in three different ways.**

- *Already examined and resolved, on the test itself.* "Replay the three recorded failed runs through the journal-alert rule on paper" carries an Issues bullet dated 2026-08-05 that resolves it explicitly: the rule it proposes is already shipped as `failed(entry) === Boolean(entry.error)` in `src/runner/journal.ts`, so a spec written against it would be green on the day it was written and the write boundary would refuse it as already-built. Its real outstanding work is a *recording*, not an instrument — a compute-only replay of 14 journals sits as an unrecorded draft with a paste-ready `ost-agent result` line in `.ost-agent/drafts/compute-docket-2026-07-24.md`.
- *The decisive half is people.* "Does a placeholder outcome get replaced…" has a compute-readable supporting half — elapsed git time between a root being created and its mandate first changed by a human, readable across the two existing vaults today — but its pre-committed threshold is "at least 2 of 3 replace the placeholder before running any process that creates nodes", which requires three people handed a scaffolded vault. No exit code reaches that. Its frontmatter carries no lane and its body says "**Lane: deliberately unset**", so it is in neither the ask queue nor any labelled count.
- *The measurement is outside this repository.* "Count how many of the operator's real experiment sources can push anywhere at all" is an afternoon reading third-party product documentation against the plans the operator is actually on. Nothing in this product's suite can observe another vendor's webhook support.

**The correction to the method, which is the part worth keeping.** The enumeration that produced the 67 matches the frontmatter block whole and excludes any file carrying `instrument:` or `lane:`. That predicate is exact and it is blind to an examination recorded in *prose*: the journal-replay test was examined and resolved four weeks before this census listed it as genuinely unexamined, and it was listed because resolving a test as non-instrumentable leaves no frontmatter trace. So the census's "genuinely unexamined" figure is an upper bound on unexamined work, not a count of it, and the same blindness applies to however many of the remaining five carry a prose resolution nobody has re-read. Taking the one confirmed instance out, the live unexamined residue is **five**.

**Running total across all passes.** 17 of the 21 non-people entries have now been examined, and the count of instrumentable ones is still **zero**.

**Limits.** Three of eight is not a rate over the eight, and the selection was deliberately biased toward the instrumentable, which makes zero a conservative result rather than a flattering one — but it is three files, not a population. The "already resolved in prose" blindness is demonstrated on one file; how many of the other five share it was not checked. The five remaining are unread by this pass. Nothing was executed, no lane set, no instrument set, no rung moved, no status changed, and no node created.

_Method: three AssumptionTest bodies and two Solution bodies read in full from disk, plus first-party `ost_read_repo` reads of `src/knowledge/instruments.ts`, `src/ost/instrument.ts` and `src/ost/red-now.ts`. Observed structure of files on disk; it grounds feasibility, not demand. `ost_check` is withheld on this surface, so this write is unverified by the invariant checker by design._

## 2026-09-02 — the residue is now zero: all 21 non-people entries examined, none instrumentable

Four lines, per this node's convention, and it closes a question this node has carried since 2026-08-29. The findings are on the four tests themselves and are pointed at rather than restated here.

**The residue named in the 2026-09-01 section is exhausted.** That section listed eight genuinely-unexamined tests; a later firing examined "Give a cold session only the tree and see whether it can say why the work exists" and corrected the live figure to four. This pass read the remaining four in full — "Settle the known prompts as config and count how many new ones appear in a month", "Follow a candidate source list for a month and count items that bear on anything open", "Set up one scheduled export and check every week whether it is still arriving", and "Two unattended weeks - count pages, grind, and money burned". **All four are non-instrumentable, and each carries the verdict and its specific reason on its own body.** The reasons are four different ones, not one repeated: an arrival rate over wall-clock; a person's judgement of relevance; a third-party producer's persistence; and a conjunctive threshold whose four computable bars are held hostage by a fifth that names the operator's judgement.

**So the sampling stops here.** Across all passes, **21 of the 21 non-people entries in the unlabelled 67 have now been examined, and the count of instrumentable ones is zero.** Every prior statement of that was a sample declaring its own bias; this one is an enumeration over the whole non-people set. The claim that remains a classification rather than a reading is the 46 people-shaped entries, sorted by what their titles name as the measuring act — and no pass has found a title-based read of that kind to be wrong yet.

**What this settles, and what it hands the operator.** `solutionsMissingInstruments` is not a backlog with a low yield; on the portion anyone has been able to check, its yield is exactly nil, and the reported figure measures how many solutions exist rather than how much work is owed. The concrete move is unchanged and is now larger: every one of these needs `ost-agent lane --set`, which is withheld from this surface, and the four examined today each carry their paste-ready repair. One of them, "Two unattended weeks - count pages, grind, and money burned", additionally states a prerequisite (the exit-0 defect) that nothing on the frontmatter records, so it does not appear in `blockedOnPrerequisite` either.

_First-party to this firing: four AssumptionTest bodies read in full from disk, plus this node and two Solution bodies. Observed structure of files on disk; it grounds usability, not demand. Nothing was executed, no lane set, no instrument set, no rung moved, no status changed. `ost_check` is withheld on this surface, so this write is unverified by the invariant checker by design._
