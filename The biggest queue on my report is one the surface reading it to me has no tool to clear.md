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
