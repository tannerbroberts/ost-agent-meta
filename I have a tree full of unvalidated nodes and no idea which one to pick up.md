---
type: Opportunity
status: unvalidated
source: 'RUNTIME:tetrix-ost@2328e61 (2026-07-24 14:37–16:46) — observed second instance'
created: '2026-07-25'
evidence: assertion
authorship: machine
---
#Opportunity #ported-from-ost-agent-vault #evidence/assertion
[[Show me the whole priority order, and why each item sits where it does]]
[[Nothing names the one node to pick up next, so choosing is work before the work]]
[[The queue sends me to ideate under a heading that already has thirty solutions under it]]
[[The work waiting on me has no start date, so I can't tell what has been waiting longest]]

**Customer need (operator's perspective):** "I poured compute into this and came back to forty nodes that all say `unvalidated`. I believe them. I still don't know what to do on Monday morning."

## Evidence — observed, not inferred

This is the first opportunity in this tree grounded in a *running instance* rather than in design docs. A second OST-Agent instance ran unattended against `~/dev/tetrix-game-monorepo` from 14:37 to 16:46 on 2026-07-24, writing to the `~/dev/tetrix-ost` vault. It produced a genuinely good tree: 5 top-level opportunities, 17 solutions, 21 assumption tests, every node sourced, every claim hedged appropriately.

Then it hit a wall. Having nothing left to create, its final acts (commits `bfa741b`, `2328e61`) were two long prose annotations on the root Outcome node. The second one opens by diagnosing itself:

> "This tree now contains 5 top-level opportunities, 17 solutions and 21 assumption tests, all unvalidated, and it offers a builder no way to tell which one to pick up. **That is a real defect in the artifact.**"

The agent then hand-wrote, in prose, the prioritization the tool surface would not let it express: that one assumption test ("Can we tell a real arrival from a refresh") is worth building first because four other tests across an entire top-level opportunity pre-commit to thresholds that today's instrumentation physically cannot read. One build unblocks four. It found a genuine leverage ratio — and had no structured place to put it.

Corroborating detail: the agent also invented its own tag vocabulary to carry priority information the schema doesn't model — `#unblocks-discovery`, `#prerequisite`, `#feasibility`, `#agent-executable` — and then flagged its own invention as a hazard: an agent that tags the work it can do alone "would steer this product toward measurement and away from customers." Ad-hoc vocabulary invented under pressure is a schema gap announcing itself.

**This vault has the same defect.** 49 nodes, 24 of them `unvalidated` assumption tests, no ordering. A builder reading it today would pick by scroll position.

## Why this is the load-bearing opportunity right now

The outcome for this product is that a stakeholder can pour compute into a goal and *trust it to efficiently map out the path to accomplishing the goal*. Mapping is now demonstrably solved — two independent runs produced defensible trees. What is not solved is that the map has no legend. Every other opportunity in this tree concerns whether the operator can *trust* the artifact. This one concerns whether the artifact does anything for them once trusted. Trust in an inert artifact is worth nothing.

**Litmus (is there more than one way to address it?):** Yes, and they are genuinely different: rank by unblocking-leverage; model prerequisite edges between tests so ordering falls out of structure; maintain a standing "next build" node the agent rewrites each pass; score by information-gained-per-unit-cost; force pairwise comparison. These trade off against each other. It is a real opportunity, not a solution in disguise.

_Provenance: direct observation of a second OST-Agent instance's vault and git history, 2026-07-24. Unvalidated — no operator has said this out loud yet; it is inferred from an agent's self-diagnosis and from this vault's own shape._

## History
- 2026-07-24 evidence: (none) → observed — retro-labeled: recorded-as-it-happened incident in this vault / tetrix-ost with commit-level provenance
- 2026-08-01 evidence: observed → assertion — demoted by the fifteenth pass — B3's rung-unearned guard (v0.23.0-line) shipped after this node was authored; its source is not a TRANSCRIPT: recording, so 'observed' was unearned. Demotion only, per rungs.ts's own remedy.
- 2026-08-05 unlinked "A standing Next Build node the agent rewrites every pass" — re-parented under "Nothing names the one node to pick up next, so choosing is work before the work" — this solution answers that need, not the categories beside it
- 2026-08-05 unlinked "Prerequisite edges between assumption tests" — re-parented under "Nothing names the one node to pick up next, so choosing is work before the work" — this solution answers that need, not the categories beside it
- 2026-08-05 unlinked "Rank every node by how many blocked tests one build would unblock" — re-parented under "Nothing names the one node to pick up next, so choosing is work before the work" — this solution answers that need, not the categories beside it

## Issues
- 2026-07-25 Mirror flag: near-duplicate pain with 'Nothing kills a candidate, so every idea I have ever had is still alive' — see that node's annotation. Merge-candidate pair for human decision (2026-07-24 review).
- 2026-08-06 Scope judgement by the 2026-08-06 unattended sweep, recorded so a human can overrule it. The sweep was asked to ideate up to three solutions for each of 28 under-served opportunities — roughly 78 new solutions, each needing an assumption and a test, so ~230 nodes. It stopped after two opportunities (six solutions, six assumptions, six tests, all grounded in evidence ingested in the same pass) and did not mass-ideate the rest.

Reason: the tree already holds 267 solutions and 275 tests, of which 0 have been tested and roughly 10% are built. The stated need on this node is that there are too many unvalidated nodes to choose between. Adding 78 more agent-ideated candidates, none of which anyone asked for and none of which would be tested either, is the mechanism of this opportunity operating rather than a response to it — the queue would be satisfied and the customer's problem made worse.

The two opportunities that were served were chosen because this pass had fresh first-party evidence for them, not because they ranked highest: "The same agent has a different tool surface on every surface I run it on" and "Each pass leaves me more to check than it started with".

What a human should decide: whether under-served counts are worth clearing at all on a tree this size, or whether the minimum-solutions rule should be scoped to opportunities somebody has actually chosen to target. Torres's own work-in-progress limit says one target opportunity at a time, which is not what a tree-wide minimum produces.

## Supporting evidence — builder verdict (2026-07-24)

`INBOX:2026-07-24-builder-evidence-debt-gate-verdict.md`: the evidence-debt gate, run against this tree, blocked every solution it had shipped — `Solutions: 24 (untested 0, proposed-only 24, tested 0)`. The gate turned this opportunity from a feeling into a measurement: nothing in the tree was runnable-next because nothing had a recorded result. Evidence class: observed behavior (the gate's own output). This item creates no new opportunity — it is direct evidence for this one.

## Supporting evidence — an operator said it out loud (2026-07-25)

The provenance note above records that "no operator has said this out loud yet; it is inferred from an agent's self-diagnosis." That is no longer true. The founder, in conversation on 2026-07-25: "I want to be able to see a clearly prioritized list from top to bottom. Not just what is the highest leverage — but also, why." Still a founder source (non-external), so the rung is unchanged, but the need is now stated by a human rather than only inferred from vault shape. The statement also sharpened a facet the solutions here did not cover — a complete ordering with legible per-item rationale — captured as the child opportunity "Show me the whole priority order, and why each item sits where it does".

## A second marker with the same defect, and this one was added to discriminate (2026-08-30)

The opening quote on this node is about `unvalidated`: forty nodes all carrying one label, and no way to choose between them. That framing treats the problem as a side effect — `unvalidated` is a *status*, and its being near-universal is a consequence of nothing having been promoted. The authorship field is the same defect in a field whose entire purpose was to tell nodes apart, and it is worth recording because it shows the failure is not incidental to this one status value.

**Read off `ost-agent rollup` this pass**, over 1556 nodes:

- `0` carry human-written prose
- `164` are labelled machine-only
- `1392` are unlabelled, having been written before authorship was recorded

The rollup states the consequence in its own words: *every one of those 164 labelled nodes reads the same — a marker true of all of them is not telling a reader which is which.*

**Why this is worse than the `unvalidated` case rather than another example of it.** A status that is universally `unvalidated` is at least *accurate*, and it becomes informative the moment a human promotes something — the mechanism to differentiate exists and simply has not fired. Authorship has no such path from here. It partitions the tree into "machine" and "not yet asked", and the second class is 89% of the tree and shrinks only if someone relabels 1392 nodes by hand. A reader wanting to know which claims a person actually stood behind gets the same answer on every node they check, and will stop checking — which is precisely the "builder would pick by scroll position" behaviour this node already records, arriving through a different field.

**What it implies for the solutions beneath this node, stated as a caution rather than a ranking.** All three children — leverage ranking, prerequisite edges, a standing next-build node — are ordering mechanisms that read node attributes. An attribute that is constant across the corpus cannot contribute to any ordering built on it, so authorship is not available as an input to any of them today, however sensible it looks in a schema. Whoever designs the ordering should check which fields are actually varying before conditioning on them; this tree currently has fewer discriminating fields than its schema suggests.

**Not proposed, and deliberately so.** The obvious repair — backfill authorship across 1392 nodes — is a bulk rewrite of provenance on claims nobody has re-read, which is the sort of thing that makes a field *look* informative without anyone having actually stood behind the nodes it now credits. That is a human's call about their own attribution, not an unattended pass's, and it is not recommended here either way.

_Source: the `ost-agent rollup` output this firing was given, computed from the nodes rather than summarised by anyone. Observed property of this vault's own artifact; grounds usability, not desirability. No test was run, no result is recorded, and this node's rung is unchanged at `assertion`._
