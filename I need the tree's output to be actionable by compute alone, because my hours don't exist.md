---
type: Opportunity
status: unvalidated
source: >-
  founder-directive:2026-07-24 — compute-only actionability, stated in session
  as first operator
created: '2026-07-25'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[Triage every assumption test by the human-minutes it actually needs, and let compute run the zero-minute lane]]
[[Weekly ten-minute docket - every pending decision arrives prepared as one yes or no]]
[[Scheduled ambient passes that page the operator only at hard gates]]
[[Leave a permanent test behind instead of a one-off verdict draft]]
[[Every run ends blocked on a credential only I hold]]
[[The whole loop waits on one human command, and nobody is told it is waiting]]
[[The work I most want to run unattended is the work that keeps needing a decision]]

**The need (operator's voice):** "I'm a working man, husband, and father of three, soon to be four. I prioritize my family, but there's no excuses that build new products. The output from my OST needs to be actionable by me pointing my Claude subscription's token generation power at the problem. I need better bootstrappability from the agent with less involvement from me."

**Why it matters:** This is the first opportunity in this vault sourced from a real operator describing their own binding constraint in actual use. The constraint is structural, not motivational: the current critical path (cold-offer test) budgets ~4 operator-hours; the test backlog assumes a human with afternoons. If solutions are only actionable by a human with hours, this tree steers work that will never happen — for this operator and plausibly for the entire solo-founder segment.

**The honest floor (recorded at birth):** compute cannot absorb four things — the operator's identity in outreach (consent), money, validation authority (the proposer must never dispose), and the goal itself. The need is therefore precisely: human involvement measured in MINUTES at decision-shaped moments, never in hours at work-shaped ones. "Zero" is not on the table; "minutes" is the spec.

**Rung honesty:** assertion — the operator is also the founder, so this is a claim from inside the building. It carries unusual weight anyway: it is a first-person account of a verifiable constraint (time scarcity), not a theory about other people's needs. First non-founder confirmation would come from any outside operator citing the same constraint.

**Litmus (more than one way?):** yes — compute-runnable test triage, prepared decision dockets, exception-paged autonomous loops, delegation protocols are all distinct answers.

## Issues
- 2026-07-25 Cross-branch: this need REFRAMES the cold-offer critical path rather than replacing it — outreach identity/consent stays human, but compute compresses the operator's share from ~4 hours to ~45 minutes (sourcing sweep, all 20 personalization drafts, tracking, reply filing, verdict prep are all compute). Also gates 'Scheduled ambient passes…' behind the exit-0 fix tracked under 'A failed pass reports success, so my automation can't tell'.
- 2026-08-04 INSTRUMENT DEBT IS MOSTLY NOT INSTRUMENT DEBT (2026-08-04, unattended pass). The sweep reports 243 solutions whose tests are prose only, framed as one backlog to be cleared by declaring an `instrument:`. This pass read 19 of those test nodes in full and could honestly instrument 5. The other 14 are not tests missing a command; they are questions no command can answer, and they fall into three shapes that want three different remedies.

**Shape 1 — a person's judgement over records already held (8 of 19).** Blind-rating a model's reading, marking a near-miss suggestion correct or misleading, reading a migration diff for changed meaning, ranking past questions by consequence with hindsight, scoring five degraded-pass reports where the node explicitly bars the authoring agent from judging. These are cheap and retrospective, but the measurement is a reader. No spec substitutes for one.

**Shape 2 — compute-runnable analysis that is still not a spec (2 of 19).** `Draft the decision classes from the older half of the stops and test them on the newer half` says in its own Cost line that "a session with no human present can run it end to end". It is a hold-out classification over transcripts already committed. It wants the `runnable` lane, not an instrument — and this surface cannot put it there. `ost_flag_humans_required` only ever removes work from compute's reach; the permissive direction is a human's `ost-agent lane --set`. So the tests most ready for compute are exactly the ones an unattended pass is powerless to release.

**Shape 3 — a real environment a spec cannot stand up (2 of 19).** `Check whether a toolless session can even run the tool check` has to reproduce a scheduled run with the plugin absent; the question is whether the check executes at all in the environment where the thing it checks is missing, and a spec running inside a working suite is the one place that cannot be asked.

**One outside-the-building interview** and one viability arithmetic make up the rest.

**A second observation, verified in this pass rather than reasoned.** Setting an instrument does not move a test out of `needsHumans`. All five tests instrumented this pass — `Add the hook and check whether the commit paths a run actually uses all pass through it`, `Audit every consumer of the tree for whether it would honour a retraction flag`, `Kill ten runs at random points and check what the journal's last line claims`, `Replay the four toolless passes and see whether the check names the right file`, `Can a pass tell a human edit from its own, using only git` — still appeared under `assumptionWork.needsHumans` on the next sweep. That is probably correct behaviour, since a permit needs an observed failure from `ost-agent verify`, but it means the two counts move independently and neither one alone says what is buildable.

**What this suggests a human should weigh.** If the ~26% instrumentable rate observed here holds across all 243, then roughly 60 of them are genuine instrument debt and roughly 180 are tests that will report as missing an instrument forever, because the thing they lack is a lane, a reader, or an environment. That is the same shape as the stranded-evidence backlog already recorded on [[A Context node type for evidence that is true, useful, and not a customer need]]: a queue that cannot be emptied by any action available to a pass, standing under a heading that reads as debt. The cheap partial fix is not a new node type here but a triage verb — some way for a pass to record "this test's question is not spec-shaped, and here is which of the three shapes it is" — so that the count of solutions genuinely awaiting a command is separable from the count awaiting a person. The rate itself is a sample of 19 taken alphabetically, not a census; a human should discount it accordingly.

Recorded by an unattended pass. Nothing here was tested and no threshold was met.

## Observed instance — 2026-07-25 autonomous loop, and exactly where it hit the wall

One unattended run took both products from tree to shipped code with **zero operator minutes**: read both vaults, picked each tree's stated next build, wrote tests first, implemented, ran the suites, and pushed. Concretely — `ost-agent` v0.5.0 (the exit-code/status fix) and `tetrix-game-monorepo` `8e6d50c` (the anonymous-funnel instrument that unblocks four assumption tests). This is the strongest observed evidence yet for this need's central claim: compute can absorb the *work* shape.

**Then it hit the honest floor recorded at this node's birth, precisely where predicted.** `npm publish` needs a credential the loop does not have and should not have (`npm whoami` → `ENEEDAUTH`, no `NPM_TOKEN`). RELEASING.md's alternate path — publish a GitHub Release, which fires the publish workflow — was also unavailable, because the environment's git proxy rejected the tag push, so the tag that workflow keys on never reached the remote. **The release commit is on `main`; the package is not on npm.** Filed as `INBOX:2026-07-25-friction-npm-publish-cannot-complete-in-the-unattended-lo.md`.

**Why this sharpens the need rather than just confirming it.** The floor said compute cannot absorb identity, money, validation authority, or the goal. This adds a fifth, and it is not one of those four: **the credential that makes work public.** Publishing is not a decision — nobody is weighing anything, and there is nothing for the operator to judge. It is a one-minute mechanical act that only a credential-holder can perform. The spec "minutes at decision-shaped moments" does not cover it; this is a minute at a *permission*-shaped moment, and a pipeline that hands off decisions cleanly will still stall here.

**What that implies for the candidates below.** [[Weekly ten-minute docket - every pending decision arrives prepared as one yes or no]] is built for decisions and would carry this badly — "run `npm publish`" is not a yes/no with evidence behind it. Either the docket grows a distinct *pending permissions* lane (chores, not judgements), or credential-holding steps are pushed out of the loop's path entirely (an automation token in CI, triggered by something compute can reach). A human should pick; the agent should not quietly acquire publish rights, and did not.

## Observed instance — 2026-07-25, second loop of the day: compute ran a lane, on the other product

A second unattended run shipped to both products with **zero operator minutes**, and it is worth recording separately from the first because it produced a different *kind* of evidence.

The first run showed compute can absorb the work shape of *building*. This one showed compute can absorb the work shape of **verifying** — which is the half this node's leading candidate is actually about.

**What happened.** The tetrix tree's standing briefing named its highest-leverage next action as a ~15-minute human task: walk five journeys against a live Postgres, because the funnel instrument's real SQL had never executed. The loop did it without a person: found no Docker daemon, found PostgreSQL 16 server binaries on the box instead, initialised a cluster, applied all 23 migrations, and converted the five-journey hand-walk into `visitorFunnelService.pg.test.ts` — 16 checks against the real database, green, re-run on every `pnpm test`.

**Why that is stronger evidence than "a test was written".** The task was *classified by a previous pass as needing a human*, with a time estimate attached. It did not need one. That is a mislabel in the safe direction — exactly the direction the v0.6.0 lane rules force — and it is the first concrete case of the compute-only lane paying, on a product that is not this one.

It also sharpens what the lane triage is for. The saving is not the fifteen minutes. It is that a hand-walk verifies one afternoon and a test verifies every commit forever; the lane triage's real product is *converting expiring human verification into non-expiring mechanical verification*, and the fifteen minutes is a rounding error next to that.

**The honest limit, recorded so this is not read as more than it is.** No defect was found, so the run produced no news. A verification lane that only ever confirms is cheap to run and worth very little; the case that matters is one where compute finds something and a human has to decide what it means. That case has not happened yet.

**Second confirmation of the fifth floor item, and it is now a pattern rather than an incident.** `npm publish` was again unavailable (`npm whoami` → `ENEEDAUTH`), and the tag push was again rejected by the environment's git proxy — the same two failures, in the same order, in consecutive runs. v0.5.0 and now v0.6.0 both sit on `main` and neither is on the registry. Two releases of unpublished work is no longer a stall, it is a growing backlog behind one credential, and every pass that ships more code makes the eventual publish larger and less reviewable. The choice named last pass — grow a *pending permissions* lane, or push credential-holding steps out of the loop's path (an automation token in CI, triggered by something compute can reach) — is now overdue rather than open. The agent has not acquired publish rights and will not.

## Evidence (mapped 2026-07-25)

`INBOX:2026-07-24-builder-loop-stopping-blocked-on-one-human-test.md` — after five builder passes: 24 solutions, 0 tested, every candidate gate-BLOCKED, and by the system's own rules no agent may run a test. The entire loop halted on one half-day human action (hand-rating three sessions). The binding constraint was not engineering capacity but a single human-only step — the sharpest observed instance of this need. See child [[Every run ends blocked on a credential only I hold]] for the release-shaped instance.

## Fifteen recorded stops, in two sessions, from the transcript channel (mapped 2026-08-02)

`TRANSCRIPT:16e9596b-7c8f-445b-a8ff-f822ed211ea5` (8 events) and `TRANSCRIPT:7e982096-36c5-4ac2-a23f-75865bc4bf8e` (7 events) contain no tool failures at all. Every event is an `AskUserQuestion` — the pass halting the work to ask a human. The questions, in the order they were asked: whether "only serve Claude subscription users" also cuts the API-key-billed autonomous runner; how the plugin should start the MCP server once npm is gone; what happens to the already-published package on npm; which workspace to implement in; what to do about a refusal message that now exists as two identical string templates; what to do about a command that the next task deletes anyway; and how to close evidence ingestion, severed when the runner was deleted.

**What this adds to this node.** Its honest floor already names what compute cannot absorb — a decision reserved for a human, a credential, a permission. These fifteen stops are a different shape and worth separating out: **not one of them is a permission or a secret.** Each is a design choice with more than one defensible answer, and the pass could not tell which of them were the operator's to make and which were its own. The cost is not that a human was needed. It is that the pass could not distinguish the two, so it escalated all of them — and a pass that escalates every fork in the road needs a human continuously, which is the condition this node exists to remove.

**Deliberately not proposed as a new opportunity.** Two sessions, one corpus, and both are sessions *building the product* rather than running a discovery pass on a vault — the wrong population for a claim about operators. A second sighting inside a session that is actually running a pass would make it a pattern rather than an observation. Flagged here for a human to weigh; a human may reasonably decide it is already a distinct need.

Rung `observed` on this vault's own sessions, per each record's `TRANSCRIPT:` provenance; explicitly not demand evidence.

## What the instrument backlog turns out to be made of (observed 2026-08-04)

An unattended pass worked through the `solutionsMissingInstruments` list — 206 solutions whose tests are prose only — expecting the gap to be *omission*: tests that could have named a command and nobody had written one. That is not mostly what it is.

Of the first 25 solutions on the list, only about eight carried a test a spec could honestly settle. The other seventeen name a person as the measurement, and they do so correctly: "Ask five operators whether they would put their secret in a broker", "count who comes back a second time unasked", "have three independent judges nominate for ten solutions", "do written reasons get challenged, or only read". Those are not lazy tests. They are the right test for the risk, and no command can stand in for them.

**So the backlog is not one problem, it is two, and they need separating before anyone works it.**

The first is genuine omission — a mechanical question with no command attached — and it is the smaller half. The second is a mismatch: a **mechanism-shaped solution carrying a belief-shaped test**. "A spend ceiling per period that stops the loop dead" is a guard; its only test is "read back four weeks of spend and judge how much bought something worth having". "A whole-tree ranked ledger that refuses to publish a row without its reason" is a refusal; its only test is "do written reasons get challenged, or only read". In both, the human study is a good question about whether the thing is *worth having*, and neither touches whether the mechanism *works*. A builder handed either node still has no definition of done, and adding an instrument to the existing test would not fix it — the instrument would be measuring something the test never asked.

This matters for this need specifically. Compute-alone actionability was being read as "every test gets a command". It cannot be, and pursuing it that way would produce commands that pass while proving nothing — which is worse for this need than an empty field, because an empty field is visibly empty.

The version that survives contact: **every solution needs one test whose verdict a machine can reach, and may need a second that only a person can answer.** Those two live at different layers of risk — does it work, versus is it worth having — and the tree currently forces them to share a node. Whether that means a second test per solution, or a typed distinction between the two kinds, is a design question this pass is not entitled to settle.

Evidence class: this is a census of the tree's own contents by a pass that read them, not a measurement of anything outside. It is an assertion about the artifact, and it should be checked by rereading the list rather than believed on the strength of having been written down.

## Why the instrument backlog is 195, measured rather than estimated — unattended sweep, 2026-08-04

`ost_next_work` reports 195 solutions whose tests are prose only. That number reads like a backlog of unwritten commands. It is mostly not.

**The exact counts, read off the vault's own files.** 249 assumption tests exist. 54 carried an `instrument:` before this pass and 6 more were added by it, leaving 189. The 54 already instrumented are, almost without exception, the tests whose titles begin with a mechanical verb — *Count*, *Replay*, *Check*, *Time*, *Audit*, *Sweep*. Earlier passes worked that seam and it is close to exhausted. What remains is dominated by tests that name a person as the measurement: *Ask ten buyers…*, *Interview ten solo builders…*, *Have a blind reader…*, *Would operators accept…*, *Blind-rate…*, *Show the operator…*. Those are not missing commands. They are correctly-written desirability tests, and forcing an instrument onto one would be a misrepresentation, not a completion.

**So the backlog is not 195 commands nobody wrote. It is a tree whose remaining questions are mostly about people** — which is the honest state of a product with, as a sibling node puts it, 212 nodes of plumbing and 0 external operators. The counter cannot distinguish "no command has been written" from "no command could be", so it will read as debt indefinitely, and passes will keep being pointed at it.

**One exact fact that has already cost a pass, worth stating plainly.** Of the 249 tests, **exactly one** carries an explicit `lane:` field. Every other test is reported by `ost_next_work` under `needsHumans`, and that is the *default*, not a judgement anyone made. A pass on 2026-08-04 read the default as a deliberate classification, concluded the lane data was meaningless, and swapped a good instrument off [[Can riskiest-assumption-tested be judged mechanically]] before catching itself and restoring it — its History records the reversal and the reason. The swap also un-cleared that test's observed red. Any pass reading `assumptionWork` should treat `needsHumans` as "unclassified" and read the node instead.

**What this sweep could not do, and it bounds every instrument written here.** An instrument must be red the day it is written, and this surface cannot verify that: reading the product repository is off the unattended path, and `ost-agent verify` — the only thing that can record an observed failure — is not on it either. The six instruments added this pass are all of one safe shape: a spec file that does not exist, for a mechanism the solution's own body says is unbuilt, so `vitest` exits 1 on "No test files found". That is genuinely red, and it is red for the weakest available reason. **None of them is a build permit and none should be treated as one until `ost-agent verify` has watched each fail.**

**What would actually move this row.** Not more instruments. Either a way for the sweep to distinguish "un-instrumentable by design" from "un-instrumented", or an accepted convention that a human-lane test is a *finished* test rather than a gap — at which point the 195 becomes something like 60 and the number starts meaning what a reader assumes it means.

Evidence class: a census of this vault's own files, taken by the pass that worked the bucket. Assertion about the artifact, not a measurement of anyone's behaviour.

## The mechanical-verb seam was not exhausted — it was being searched by the wrong key (unattended sweep, 2026-08-04)

The section above concluded that earlier passes had worked the mechanical seam "close to exhausted", on the evidence that the already-instrumented tests were almost all the ones whose *titles* begin with *Count*, *Replay*, *Check*, *Time*, *Audit*. That inference was sound about what had been done and wrong about what was left, and the correction is cheap enough to be worth recording because it tells the next pass where to look.

**Searching by title was the mistake. Searching by `threshold:` finds a different set.** This pass selected candidates by a mechanical property of the file rather than by the shape of the sentence: tests carrying a `threshold:` field and no `instrument:`. That set is large, and a substantial fraction of it is instrumentable. Thirteen instruments were written from it, taking `solutionsMissingInstruments` from 184 to 167. None of the thirteen has a title beginning with a mechanical verb, which is exactly why the title heuristic missed them:

- *Try to load the tools from inside the vault directory at all* — threshold: a vault opened from an unrelated working directory yields its tools.
- *Merge the enabling config into five real project settings files and check nothing was lost* — threshold: all five keep every setting, four still parse.
- *Resume three handed-off passes from their recorded state and check they continue correctly* — threshold: same next action, no work repeated.
- *Try to confirm a tool surface without invoking any of it* — threshold: pass/fail per surface, no partial credit.

Each of those reads like a field exercise and is in fact a spec: a fixture, a call, an assertion. **The tell was never the verb. It was whether the threshold names a state of the world a process can put itself into.** *Ask ten buyers* cannot; *merge into five settings files* can, and the fact that a person would have done it by hand is a statement about who was available, not about what the question is.

**What this does not overturn.** The larger claim on this node stands and this pass re-confirmed it from a fresh sample: the majority of what remains genuinely names a person as the measurement, and the four sections above are right that the counter will read as debt indefinitely. The revision is only to the estimated size of the instrumentable remainder, which is larger than the title heuristic implied. A human should not read this as "the backlog is mechanical after all".

**One thing this pass hit that bounds every sweep like it.** Four tests were left un-instrumented on purpose because their threshold names two lanes in one sentence — a mechanical replay clause AND a clause about what a person does when shown the result. *Apply the escalating message to the five-failure session and check where it would have fired* is annotated with the reasoning. Instrumenting those would answer the cheap half and let a reader take the green for the whole, which is worse than an empty field. They need splitting, and splitting them is not this surface's call.

**And the same limit as the pass before it.** `ost_flag_humans_required` is not granted on the unattended surface, so the human-lane half of this bucket could not be labelled at all this pass — only the instrumentable half could be moved. A sweep that can add commands but cannot mark what will never take one can only ever make this row shorter, never finish it.

Evidence class: a census of this vault's own files, taken by the pass that worked the bucket. Assertion about the artifact, not a measurement of anyone's behaviour.

## What the instrument backlog actually is (measured 2026-08-05)

The sweep reports a number that reads like a writing backlog — "159 solutions whose tests are prose only" — and it is not one. The 2026-08-05 pass worked it and found the shape underneath, which is worth recording so the next pass does not re-derive it at the same cost.

**The mechanically-answerable tests have already been exhausted.** 85 tests carry an instrument, and reading their titles as a set is conclusive: they are `Replay…`, `Count…`, `Census…`, `Audit…`, `Time…`, `Kill ten runs…`. A prior pass harvested every test a spec file could settle. What is left in the 159 is the residue, and its titles are the opposite kind: `Ask ten PMs…`, `Interview ten solo builders…`, `Would operators…`, `Have a blind reader…`, `Blind-rate…`, `Offer a maintained tree at a stated monthly price…`.

**Sampled hit rate: roughly 1 in 5, and falling.** Of the 25 solutions on the sweep's first page, 20 rest on a test where a person's reaction *is* the measurement. Of a second, deliberately optimistic sample of five chosen because their titles looked mechanical, four turned out to name a human in their design — "three reviewers independently rank eight branches", "a human marks by hand which nodes they consider stale", "a human performs the transcript comparison; the agent must not score its own reporting rate". Only one was genuinely instrumentable.

**So the number will not go to zero, and chasing it is how a pass does harm.** Two failure modes are already on the record. This vault contains a History line reading "the preceding replacement in this History was made in error, from misreading the default `needsHumans` lane as an instrument gap" — a prior pass churning instruments onto tests that already had them. And two nodes in the 159 cannot honestly take an instrument at all because their subject already shipped: [[Replay the three recorded failed runs through the journal-alert rule on paper]] describes a rule that is live in `src/runner/journal.ts`, and [[Test can a full pass be done with no delete or edit tool]] asks whether append-only suffices, a question the arrival of `ost_edit_node` and `ost_merge_nodes` appears to have answered. A spec written for either would pass on the day it was written, which is the one property that makes an instrument worthless.

**What the residual number actually measures.** Not unwritten commands — unbought hours. Every one of those 159 is a solution whose only path to evidence runs through a person doing something, and this opportunity's whole premise is that those hours do not exist. That reframes the backlog from a task into a finding: **the tree has generated far more demand for human measurement than the operator can ever supply, and no amount of compute closes the gap.** The honest responses are to prioritise ruthlessly among the human tests rather than treating all 159 as owed, or to prefer candidates whose riskiest assumption is feasibility — because those are the ones compute can actually settle.

A useful next measurement, and a cheap one: partition the 159 by the risk category their test names. If desirability and viability dominate, that is this opportunity's core claim quantified rather than argued.

_Recorded during the 2026-08-05 unattended pass. Assertion — this is the agent's own analysis of the tree, not an outside finding._

## The limit now has a rate attached — 2026-08-05 sweep

Previous entries recorded that `ost_flag_humans_required` is ungranted on the unattended surface. This pass measured what that costs, by triaging the backlog node by node instead of skimming it.

Thirty-three assumption tests were read in full and sorted by what could actually settle them:

| Disposition | Count |
| --- | --- |
| Repo-answerable — an instrument was written | 9 |
| Irreducibly a person (interview, consent, blind rating, a builder's own choice) | 17 |
| Already correctly dispositioned by an earlier pass, or would go green on arrival | 4 |
| Two lanes in one threshold — a command would answer the cheap half and hide the load-bearing one | 3 |

**Roughly one in four of what remains can take a command; over half can never take one.** That ratio is the finding, and it changes what "work the backlog down" means. The residual is not a queue of un-instrumented tests waiting for effort — it is mostly a queue of *correctly* un-instrumented tests waiting for a label this surface cannot apply. A sweep that can only add instruments will asymptote at the ratio above and then report the same number forever, with nothing left that it is permitted to do.

The three two-lane entries are the interesting minority, because they are neither. Each names a mechanical clause and a human clause joined by "and", so a single command goes green on arithmetic nobody doubted while the clause the solution lives or dies on stays untouched. Splitting them is the fix and it is a write this sweep does not have either — creating the split node is out of scope and labelling the human half is ungranted. They were annotated in place instead: see the note on [[Count how many past releases a push-first rule would have blocked]] for the worked example.

Evidence class: a census of this vault's own state, taken by the pass that hit the limit. Assertion about the artifact, not a measurement of anyone's behaviour.
