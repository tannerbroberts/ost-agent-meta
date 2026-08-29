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
