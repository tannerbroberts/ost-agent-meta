---
type: Opportunity
status: unvalidated
evidence: observed
source: 'RUNTIME:tetrix-ost@2328e61 (2026-07-24 14:37–16:46) — observed second instance'
created: '2026-07-25'
---
#Opportunity #ported-from-ost-agent-vault #evidence/observed
[[A standing Next Build node the agent rewrites every pass]]
[[Prerequisite edges between assumption tests]]
[[Rank every node by how many blocked tests one build would unblock]]

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
