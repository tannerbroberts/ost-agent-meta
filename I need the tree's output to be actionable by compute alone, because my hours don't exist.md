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

**The need (operator's voice):** "I'm a working man, husband, and father of three, soon to be four. I prioritize my family, but there's no excuses that build new products. The output from my OST needs to be actionable by me pointing my Claude subscription's token generation power at the problem. I need better bootstrappability from the agent with less involvement from me."

**Why it matters:** This is the first opportunity in this vault sourced from a real operator describing their own binding constraint in actual use. The constraint is structural, not motivational: the current critical path (cold-offer test) budgets ~4 operator-hours; the test backlog assumes a human with afternoons. If solutions are only actionable by a human with hours, this tree steers work that will never happen — for this operator and plausibly for the entire solo-founder segment.

**The honest floor (recorded at birth):** compute cannot absorb four things — the operator's identity in outreach (consent), money, validation authority (the proposer must never dispose), and the goal itself. The need is therefore precisely: human involvement measured in MINUTES at decision-shaped moments, never in hours at work-shaped ones. "Zero" is not on the table; "minutes" is the spec.

**Rung honesty:** assertion — the operator is also the founder, so this is a claim from inside the building. It carries unusual weight anyway: it is a first-person account of a verifiable constraint (time scarcity), not a theory about other people's needs. First non-founder confirmation would come from any outside operator citing the same constraint.

**Litmus (more than one way?):** yes — compute-runnable test triage, prepared decision dockets, exception-paged autonomous loops, delegation protocols are all distinct answers.

## Issues
- 2026-07-25 Cross-branch: this need REFRAMES the cold-offer critical path rather than replacing it — outreach identity/consent stays human, but compute compresses the operator's share from ~4 hours to ~45 minutes (sourcing sweep, all 20 personalization drafts, tracking, reply filing, verdict prep are all compute). Also gates 'Scheduled ambient passes…' behind the exit-0 fix tracked under 'A failed pass reports success, so my automation can't tell'.

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
