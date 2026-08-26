---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-25-friction-ost-next-work-demands-solutions-under-7-opportun.md'
created: '2026-08-02'
evidence: assertion
authorship: machine
---
#Opportunity #unvalidated #evidence/assertion
[[Split the outstanding list by who may act on it, and report only this actor's share]]
[[An acknowledgement that records a decision not to act, and takes the item off the sweep]]
[[Items age out of the default view into a backlog that is counted but not reported]]

Some opportunities in a tree are deliberately held: they carry an evidence-debt or prioritization gate written into their own bodies, saying in effect "do not ideate here until X". The outstanding-work counter cannot read that governance, so it reports the same seven items as needing solutions on every run, forever.

That puts the operator between two bad outcomes. An obedient quota-filler trampled the gate it was told to respect; a governed pass reports identical outstanding work every time and never reaches done. Either way the counter has stopped being information — it is a standing demand that the tree's own rules forbid satisfying.

**The need:** I want the outstanding-work report to respect the holds I have already placed, so that what it lists is work I actually want done.

There is more than one way to address this: make the counter gate-aware and exclude held nodes, let a node declare a hold the tooling can read as a field rather than prose, report held items in a separate section that does not block done, or expire holds after a stated condition so they cannot become permanent silence.

## Provenance

Distilled from `INBOX:2026-07-25-friction-ost-next-work-demands-solutions-under-7-opportun.md` — filed by the twenty-passes ambient driver against 5 strategic opportunities and 2 dogfood needs carrying explicit gates.

## History
- 2026-08-02 evidence: stated → assertion — Demoted from 'stated' for consistency: rests on an inbox friction note, and the inbox channel's earned ceiling is 'assertion'.

## Issues
- 2026-08-02 Duplicate of a prior disposition — flagged by the pass that created it, 2026-08-02. The Outcome's ledger for the twenty-passes cycle 2 (2026-07-25) records "quota-vs-gate friction → MAPPED: appended to the same node (mechanism 3)", meaning this evidence is already carried on "The pass never says it is done, so I can't tell when to stop paying for compute" — which is this node's parent. So parent and child now represent the same evidence at two levels. This pass created the node because the append had left the item showing as unmapped. Worth a human's attention beyond the merge question: this node's subject is the governance gating that the same prioritization pass established, and a pass that cannot see those gates keeps being asked to fill quotas the gates forbid — which is what happened here.
- 2026-08-05 **A second, structural instance of this — measured during the 2026-08-05 unattended pass.**

`underservedOpportunities` counts an opportunity as needing solutions when it has fewer than three **direct** `#Solution` children. It does not distinguish that from an opportunity whose solutions correctly live one layer down. So every category bucket and every mid-level parent opportunity is reported as outstanding work, permanently, and no amount of correct work removes it.

The proof is on this vault's own tree and does not require a judgement call. "The same refusal is rediscovered every session, because nothing carries the lesson forward" is listed as having 0 solutions and needing 3. Its `## History` records why: on 2026-08-05 a prior pass deliberately unlinked its three solutions and re-parented them under its child, "A correction lives only as long as the session it was given in", with the reason *"this solution answers that need, not the categories beside it."* The tree was made **more** correct, and the sweep read that as a regression from three solutions to zero.

Scale, from this pass's own numbers: of the 27 opportunities reported underserved, **17 are the Outcome's own category buckets** — the layer the `outcome-files-categories` invariant requires to exist and whose children are opportunities by definition. They can never have three direct solutions without violating the shape another gate enforces. The two gates are asking for opposite things, and a pass that satisfied the sweep would fail `check`.

The cost is exactly this node's claim. An unattended pass is instructed to handle every bucket the sweep returns; the honest response to 17 of these 27 is to do nothing; and there is no way to record "correctly empty" that the next pass will see. So each pass re-derives the same finding, or — worse, and this is the failure mode with teeth — ideates three generic solutions under a category label to make the number go down, which is how a tree acquires solutions nobody can build under needs nobody has.

**Two shapes of fix, for a human.** Either count a parent opportunity as served when its children collectively carry the solutions (roll the count down the subtree), or let the layer be declared — a bucket or parent marked as such is exempt, the way `deferred` already exempts a node from the duplicate scan. The second is narrower and matches machinery that already exists in this tool.

Recorded here rather than acted on: making the sweep stop asking is a change to what counts as done, which is governance, not maintenance.

## The same trap, now confirmed in a second bucket — 2026-08-05 unattended sweep

This node was written about `underservedOpportunities` re-demanding solutions under gated nodes. The identical failure has now been observed in `solutionsMissingInstruments`, and it is worth recording separately because the remedy a pass applied there was *designed* to clear the item and did not.

**Four of the 25 solutions this sweep was handed had already been dispositioned, in writing, by prior passes:**

- **"Refuse a wiki-link that contains a newline"** — the 2026-08-05 pass set `status: shipped` and wrote the reason into its History verbatim: it did so "because it was sitting in `solutionsMissingInstruments`, and a red-now instrument is impossible for behaviour that already ships." That was a remedy aimed squarely at this bucket. The node is `status: shipped` today and the bucket listed it again.
- **"A result must state what it did not cover"** — `status: shipped`, plus a 2026-08-04 `## Issues` note explaining at length why no instrument was written ("an instrument must be red when it is written, and this behaviour already ships"). Still listed.
- **"Append-only tool surface with no delete or shell tool"** — dispositioned twice, on 2026-08-04 and again on 2026-08-05, the second note ending "Two passes have now declined to make that call, which is itself worth knowing." Still listed. This sweep would have been the third.
- **"Post-session transcript harvester"** — a detailed 2026-08-05 note establishing the mechanism shipped and the residual test belongs to a person. Still listed.

**The mechanism is the same one established on "Evidence that fits no layer keeps coming back, so the pass never runs out of work", and generalises past evidence.** A pass's disposition is written where a *reader* looks — `## Issues`, `## History`, a status field — and the sweep computes its buckets from something else. There, mapping was readable only from frontmatter `source:`. Here, `status: shipped` is set, is correct, and is apparently not consulted by the instrument check either. In both cases the tree records the decision faithfully and the counter cannot see it.

**Why this costs more than the evidence case.** An unmapped evidence item is re-read. A dispositioned solution is re-*triaged*: this sweep read four solution bodies, four assumption nodes and several test nodes to re-derive conclusions that were already written on the nodes in full. The cost is per-pass and compounding, and it falls hardest on exactly the nodes prior passes thought hardest about.

**The concrete ask, which the three solutions beneath this node do not quite cover.** They address holds an operator places deliberately. This is narrower and cheaper: the outstanding-work computation should read the dispositions the tool's own writes already record — at minimum treat `status: shipped` as answering "why is there no instrument", since a red-now instrument for shipped behaviour is forbidden by the ruleset and the bucket is therefore asking for something no pass is permitted to supply.

_Observed by the 2026-08-05 unattended sweep across a pass boundary — the prior pass's remedy is on disk and dated, and the bucket's response to it is today's `ost_next_work` output. Grounds usability of the tool surface, not demand._

## Upgraded from inference to direct test, within one pass — 2026-08-05

The section above inferred the defect across a pass boundary: a prior pass set `status: shipped` to clear this bucket, and the bucket listed the node again the next day. That reasoning had a gap — something else could have changed in between. This sweep closed it by running the experiment inside a single pass.

**Method.** Five solutions whose bodies record a shipped version were set to `status: shipped` during this pass: "Refuse a proving command whose exit code cannot report failure" (v0.21.0, `87164d6`), "Refuse a write whose content is empty or literally undefined" (v0.18.0), "Flag a threshold that is still an instruction to choose one" (v0.10.0), "Every recorded step carries the directory and argv it actually ran with" (v0.20.0), and "Every count states the denominator it was taken over" (v0.22.0, `df5288a`). Each write returned a commit hash, so the writes landed. `ost_next_work` was then re-run.

**Result.** `solutionsMissingInstruments` returned 64 — the identical count, with the identical 25 titles shown, including both newly-shipped solutions that appear in the visible window. Nothing moved.

**So the bucket is confirmed not to read `status`.** This is the same shape as the mapping trap established on "Evidence that fits no layer keeps coming back, so the pass never runs out of work" — where a fully-cited body section was invisible because only frontmatter `source:` counts — but it is worse in one respect. There, the pass was reaching for prose and the sweep wanted a field. Here the pass wrote *the field the tool provides for exactly this transition*, through the tool's own typed setter, and the sweep still does not consult it.

**Consequence for anyone reading the number.** The 64 is not a backlog of solutions awaiting an instrument. It contains at least five that are shipped and cannot be instrumented without inventing a green-on-arrival spec the ruleset forbids, plus an unknown number whose only test is a human study. The count cannot go down through any action available to an unattended pass, so treating it as a work queue will keep producing passes that re-triage the same nodes. Two prior passes and this one have now each done that.

_Direct test on the 2026-08-05 unattended sweep: five typed status writes, each returning a commit, then one re-read showing no change. Observed behaviour of the tool surface; grounds usability, not demand._

## Read from the implementation rather than inferred from the counter — 2026-08-23 unattended sweep

Every finding above was inferred from black-box behaviour: set a field, re-run the sweep, watch the number not move. This pass read `src/eval/buildable.ts` first-party via `ost_read_repo` and can say what the filter actually does. One correction, and one new instance.

**Correction: the bucket DOES read `status`, and the 2026-08-05 null result has a different cause than the one recorded above.** `solutionsMissingInstruments` skips a solution when `status === "deferred"` and when `trustsShippedStatus(n)` holds. So the conclusion "the bucket is confirmed not to read `status`" is wrong as stated, and a pass acting on it would file a product bug that does not exist. What `trustsShippedStatus` will not do is trust the bare field — the module's own comment says why: `status: shipped` is agent-settable, so only a promotion recorded in `## History` with reasoning attached leaves the queue. That is precisely why the 2026-08-05 experiment's five typed `status: shipped` writes moved nothing: they set the field the tool provides, and the field alone was never the key. **The remedy is therefore not a code change but a different command — a human's `ost-agent promote`.** Worth having straight, because the section above ends by asking a builder to make the bucket "at minimum treat `status: shipped` as answering why there is no instrument", and that is the one reading the module rejects on purpose.

**New instance: the bucket does not read `lane` at all.** The filter is layer, `deferred`, `trustsShippedStatus`, has-tests, and has-an-instrument — there is no lane check anywhere in it. Directly beside it in the same file, `testsAwaitingVerification` does have one, `if (n.lane === CAUTIOUS_LANE) continue`, under a comment stating the principle plainly: the lane is the authority on who may run a test, and an instrument only ever says what running it would mean. The two neighbouring queues disagree about whether a human-lane label is binding.

The consequence is this node's claim in its sharpest form yet. A solution every one of whose tests is lane-labelled human-required is counted as owing an instrument **the product forbids it to carry** — the same file records that `ost_set_instrument` refuses the instrument-plus-cautious-lane combination, so the queue asks discovery for a write the write boundary is built to reject. No honest pass can ever clear such an entry, and five have now tried.

**Scale, and why this is likely most of the bucket.** `ost_next_work` reported 62 entries here this pass, alongside 454 assumption tests in `needsHumans` against 0 runnable. The tree's own answered unknown "What is in the 33 queue entries no tool has ever listed" classified the unlisted tail exhaustively and found `mechanical` = **0 of 33** — 25 `people`, 4 `elapsed-time`, 2 `shipped`, 2 `split`. A lane-aware filter is the one change that would act on that measurement rather than around it.

**The ask, narrowed.** Add the lane check `solutionsMissingInstruments` is missing, so a solution whose tests are all beyond compute's reach leaves the queue the way a `deferred` one already does. This is smaller than the gate-awareness the three solutions beneath this node propose, and unlike the `status: shipped` ask above it needs no re-litigating of what the tool may trust: the lane is human-set with `ost-agent lane --set`, so reading it is reading a human's decision — exactly the thing this node says the counter fails to do.

_First-party reads of `src/eval/buildable.ts`, `src/knowledge/instruments.ts` and `src/ost/instrument.ts` this pass via `ost_read_repo`; the `ost_set_instrument` refusal is quoted from that module's own comment rather than verified in the setter. Grounds feasibility and usability of the tool surface, not demand. No test was run and no result is recorded; the rung is unchanged._

## Correction to the section above, same pass — the lane defect is real but the yield claim was wrong

The section immediately above cites "454 assumption tests in `needsHumans` against 0 runnable" as evidence that a lane-aware filter would drain most of the 62-entry bucket. **That inference is wrong, and a builder acting on it would ship a fix with a fraction of the promised yield.** Corrected here rather than by rewriting the claim, because the underlying defect survives and only its size changes.

**What the 454 actually counts.** Read this pass from `src/knowledge/lanes.ts`: `computeMayRun` fails closed — `if (!id) return false` — so a test with *no lane field at all* reports as not-runnable and lands in the `needsHumans` bucket. The 454 is therefore "every unrun test compute may not run", which is dominated by tests nobody has classified, not by tests a human labelled.

**The measured split.** A `Grep` for `^lane:` across the vault's node files returns **exactly 50 files, every one of them `lane: humans-required`** — the same 50 the sweep reports as `outstandingAsks`. So roughly 404 of the ~454 unrun tests carry no lane at all.

**Why that guts the yield.** The check I proposed matches `n.lane === CAUTIOUS_LANE`, which is the literal frontmatter value — not the fails-closed report. A solution leaves the queue only if *every* test beneath it is one of those 50. Some of the visible 25 do qualify (their tests include "Five operators choose between sixty-one weak instruments and sixty-one blanks", "Show five operators a pass's dismissed-work list and ask whether they would have let it stand", "Blind-rate ten instruments for groundedness and compare against whether their pass had repo sight"), but most cannot, because their tests are unlabelled rather than labelled human.

**The finding that replaces it, and it is the more useful one.** The queue cannot be repaired by reading a field that 89% of its tests do not carry. Two things are needed and the order matters: the lane check is necessary but drains little today, and the binding constraint is that **404 unrun tests have never been classified at all**, so nothing downstream can distinguish "a person is the measurement" from "nobody has looked yet". Setting a lane is `ost-agent lane --set` and is human-only by design — the permissive direction is deliberately off every agent surface — so the labelling backlog is not work any sweep can take off the operator. That, rather than the filter, is why this bucket has survived five passes.

**Unchanged by this correction:** that `solutionsMissingInstruments` reads no lane while `testsAwaitingVerification` beside it does; that the two neighbouring queues therefore disagree about whether a human-lane label binds; and that a solution whose tests are all explicitly human-lane is asked for an instrument the write boundary refuses. The defect is sound; only the estimate of how much of the bucket it explains was inflated.

_First-party this pass: `src/knowledge/lanes.ts` and `src/eval/buildable.ts` via `ost_read_repo`, plus a `Grep` census of `^lane:` over the vault's own node files. Grounds feasibility and usability, not demand. No test was run and no result is recorded; the rung is unchanged._

## Narrowing the previous correction — the 404 unlabelled tests are not all human-only work (2026-08-26)

The correction above ends: *"Setting a lane is `ost-agent lane --set` and is human-only by design — the permissive direction is deliberately off every agent surface — so the labelling backlog is not work any sweep can take off the operator."* The clause before the dash is exactly right. The conclusion after it is too wide, and the difference is the size of the backlog.

**Lane labelling has two directions and only one is human-only.**

- **Permissive** — declaring that compute may run a test unattended — is `ost-agent lane --set`, a human's CLI call. There is no agent tool for it and the ruleset says there never will be, because it is the call that hands compute a permit.
- **Restrictive** — putting a test *beyond* an unattended pass's reach — is `ost_flag_humans_required`, and it is an agent tool. It takes no lane argument precisely so it can only ever move work in the safe direction.

**Why the previous pass could not see this, and it is not carelessness.** `ost_flag_humans_required` is granted by the skill and withheld from *this* surface. Verified first-party this pass in `examples/automation/autonomous-pass.sh`: `OST_TOOLS` lists 16 tools and does not include it, while the skill's `allowed-tools` declares 22; the script derives the difference and hands the pass a "What this surface withholds" note naming `ost_flag_humans_required` among the six. So an unattended firing correctly observes that it cannot label a lane, and the available inference from there — "no sweep can" — is wrong only because the sweep cannot see the surface that is wider than its own. That is this node's own thesis turned on the pass reading it, and it is worth noting that the script's comments describe the identical failure happening once before, when passes rediscovered the withheld set one denied call at a time.

**What it changes.** The 404 unrun tests carrying no lane at all split into two piles that need different actors, and only one of them is the operator's:

- Tests where **a person is irreducibly the measurement** — an interview, an offer, willingness to pay, usability with strangers. An **attended** pass holding the full skill surface can label every one of these with `ost_flag_humans_required`, no operator time required beyond deciding to run the pass. Judging from the sampling on this tree, this is the large majority.
- Tests where **compute could run it** but nobody has said so. Only these need `ost-agent lane --set`, and only these are irreducibly the operator's.

So the labelling backlog is drainable in one direction by an agent, and the bucket-clearing effect is the same either way: the lane check this node asks for reads `n.lane === CAUTIOUS_LANE`, and a test flagged human-required carries that value however it got there.

**The ask this adds, and it is cheap.** Run one attended pass whose only job is labelling — walk `assumptionWork.needsHumans`, flag the ones a person must answer, and leave the rest for the operator. That converts an unbounded human backlog into a bounded one, and it can happen before any code change to `solutionsMissingInstruments`. If the lane check does land, the two compose: the labelling makes the filter worth having, and the filter makes the labelling pay.

**Unchanged by this narrowing:** everything the previous correction established about the measured split — 50 files carry `^lane:`, all of them `humans-required`; `computeMayRun` fails closed so the 454 is dominated by the unclassified; and a lane-aware filter drains little *today*. The point here is only that "today" is a fact about what has been labelled, not about what can be, and the labelling is not blocked on the operator the way the previous wording says.

**The bound.** This is read off the automation script and the skill's declared tool list, not from running `ost_flag_humans_required` — this surface cannot call it. So it establishes that the tool is granted to the attended surface and withheld here; it does not establish that the tool behaves as its description says when called, nor how many of the 404 would survive an honest look at whether a person is really required. A pass that does the labelling should report both counts.

_First-party this pass: `examples/automation/autonomous-pass.sh` via `ost_read_repo`, plus this firing's own withheld-tools note. Grounds feasibility and usability of the tool surface, not demand. No test was run and no result is recorded; the rung is unchanged._
