---
type: AssumptionTest
status: unvalidated
source: 'agent-run:autonomous-loop-2026-07-25-pass6'
created: '2026-07-25'
evidence: assertion
authorship: machine
---
#AssumptionTest #unvalidated #potential-harm #evidence/assertion

**Assumption under test (potential harm).** That an operator handed a vault with a
placeholder Outcome replaces it before doing anything else — rather than running a
pass against it, getting a plausible tree, and leaving the placeholder in place
permanently.

**Why this is the load-bearing question for its solution.**
"Ship a starter vault whose outcome is a placeholder the human must replace" is the
only candidate that makes the founder's launch sentence literally true, and it buys
that by letting a machine write the mandate first. If placeholders get replaced
promptly, the objection to it is philosophical. If they stick, the product ships
confident artifacts about goals nobody chose — the exact failure the whole system's
"never invent the outcome" rule exists to prevent — and the solution must be killed
rather than refined.

**Proposed test, and it can be run before the solution is built.** Two existing vaults
plus any participant vault: measure, from git history, how long a scaffolded default
survives before a human edits it. `ost-agent init` already writes an Outcome from a
required argument, and `set-outcome` already records the prior mandate in the root's
history, so the elapsed time between "root created" and "root's mandate first changed
by a human" is directly readable today. Supplement with the cheapest possible probe:
give three people a scaffolded vault with a placeholder and a single instruction to
"try it", and count how many run a pass before replacing the root.

**Pre-committed threshold:** at least 2 of 3 replace the placeholder *before* running
any process that creates nodes. 1 of 3, or fewer, kills the placeholder solution
outright — not "needs a louder warning", which is what everyone proposes after a
result like that and what nobody has ever seen work.

**What it does NOT test.** Whether the placeholder helps adoption at all. A separate
question, and the one its advocates would want answered; this one asks only whether
the cost is real.

**Lane: deliberately unset.**

⚠️ Proposed only. Written by the agent that argued against the solution it protects,
which is a reason to check that the bar is not set where it is easy to clear.

## 2026-09-01 unattended sweep — examined for an instrument, and it cannot take one

Four lines, so no future pass re-derives this. This test was named in the residue of eight genuinely-unexamined tests on "The biggest queue on my report is one the surface reading it to me has no tool to clear". It has now been examined.

**Verdict: not repo-answerable.** The pre-committed threshold is "at least 2 of 3 replace the placeholder *before* running any process that creates nodes". That is three people handed a scaffolded vault and watched; no exit code from this product's own suite can observe it, and an instrument naming a spec file would fail today for a reason that has nothing to do with the question.

**One half of it is compute-readable and is not the deciding half.** The body's own design names it: elapsed git time between a root being created and its mandate first changed by a human, readable across the two existing vaults today with no new instrumentation. That is worth having and it measures the founder's own two vaults, i.e. the population least likely to leave a placeholder standing. It supports the threshold; it cannot settle it.

**One mechanical note for whoever triages.** This node's body says "**Lane: deliberately unset**" and its frontmatter carries no `lane:` field, so it appears in neither `outstandingAsks` nor any humans-required count — it is invisible to both queues while being, in substance, humans-required. That is a labelling decision and this surface holds no `ost_flag_humans_required` grant, so it is left for a human rather than acted on.

_Nothing was executed, no instrument set, no lane set, no rung moved, no status changed. Read first-party from disk during the 2026-09-01 unattended sweep._
