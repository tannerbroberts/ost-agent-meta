---
type: Opportunity
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
authorship: machine
---
#Opportunity #unvalidated #evidence/assertion
[[Every work bucket excludes nodes whose own frontmatter already says they are closed]]
[[An opportunity counts as served when its subtree has solutions, not only its direct children]]
[[A disposition record every bucket consults before it lists anything]]

A pass reaches a correct decision, writes down why, and the next pass is handed the same item as outstanding work — because the bucket that selects it has no way to represent "settled by a means other than the one this bucket expects."

The need: when a pass has correctly disposed of something, I want the next pass's work list to know that, so my compute is spent on what is actually open.

## Two faces observed on the 2026-08-06 sweep

Both were established by reading the nodes the sweep offered, not inferred.

**1. `solutionsMissingInstruments` counts shipped solutions, which can never leave it.** At least 5 of the 64 listed are `status: shipped`: "A result must state what it did not cover", "Refuse a proving command whose exit code cannot report failure", "Refuse a wiki-link that contains a newline", "Refuse a write whose content is empty or literally undefined", and "Post-session transcript harvester". Two of them carry a History line from the 2026-08-05 sweep explaining the trap in the tool's own terms — a red-now instrument is *impossible* for behaviour that already ships, because a spec asserting the guard would pass on arrival, measure nothing, and hand a builder no definition of done. That pass corrected the status instead and declined to invent one. It was right, and the item came back anyway.

This is the sharpest of the two, because the bucket does not merely waste a turn: it applies pressure toward the one thing the ruleset forbids. The only action that removes a shipped solution from this list is writing a green-on-arrival instrument. A pass under budget pressure, asked every time, eventually writes one.

**2. `underservedOpportunities` counts parent opportunities whose solution space lives on their children.** "The same refusal is rediscovered every session, because nothing carries the lesson forward" reports `solutions: 0, needed: 3`. Its three candidate solutions were deliberately re-parented onto its child "A correction lives only as long as the session it was given in" by the 2026-08-05 pass, and that node says so in its own body: it "reads as underserved in `ost_next_work` for that reason — it is a parent opportunity now, not a gap." Ideating three more solutions there would undo a considered restructuring and duplicate the child's.

Of the 30 opportunities the sweep reported as underserved on 2026-08-06, roughly half are bucket categories carrying large subtrees rather than genuine gaps.

## Why this is a sibling of the evidence face, not a duplicate of it

"Evidence that fits no layer keeps coming back, so the pass never runs out of work" establishes the same trap for `unmappedEvidence`, and establishes it better — by direct test. It should not be merged with this node, because the mechanism is different and so is the fix. There, an item is mapped only when some node's frontmatter `source:` equals the evidence id, and no tool can add a `source:` to an existing node; the fix is a place to record acknowledgement that the sweep reads. Here, nothing is missing from the node at all — `status: shipped` is already on the file, and the parent-vs-gap distinction is already derivable from the child edges. The fix is the bucket's selection predicate, not a new field.

Taken together the three faces say something the individual nodes do not: this is not one gap in one bucket, it is `ost_next_work` having no general notion of "closed", so every bucket re-derives outstanding work from scratch on every pass and each one leaks in its own way.

## What it costs

The sweep's own summary is what the loop's spend ceiling is set against. Three buckets over-report, so the pass is never done, the cadence never idles, and the operator cannot use "outstanding work" as a signal for anything. The config raised the spend ceiling 8x on 2026-08-04 to unblock exactly this queue; a queue that cannot drain will absorb whatever ceiling it is given.

⚠️ Unvalidated, and agent-observed. This is the agent reporting a defect in the surface it is graded through, which is the reflexive case the Outcome warns about — the counts above are checkable by anyone re-running the sweep, and should be checked rather than taken.

## A third face, observed by walking into it during the pass that wrote this node

The two faces above were found by reading nodes the sweep offered. This one was produced accidentally, which makes it the cleanest of the three.

This pass created "The instrument-writing step declares repo sight required and skips itself rather than inventing paths", and gave it an assumption test — "Blind-rate ten instruments for groundedness and compare against whether their pass had repo sight" — using `ost_create_node`'s `humansRequired` argument. That is the sanctioned path: the tool's own description says to use it "when a person outside the building is irreducibly the measurement", and the reason there is sound, because whether an instrument is grounded is a property of what its assertions mean against a codebase, and a missing-file red and a broken-mechanism red both exit non-zero today.

The test was created correctly, in the humans-required lane, and appears in `assumptionWork.needsHumans`. **And the solution above it immediately appeared in `solutionsMissingInstruments`, taking the count from 64 to 65.**

So a solution whose only test is *correctly* human-lane is indistinguishable, in that bucket, from one whose test is prose nobody has bothered to instrument. The bucket asks for a command, the correct answer is that no command can settle it, and giving the correct answer through the tool built for it does not register.

**Why this is the sharpest face of the three.** The other two waste a turn re-deciding something. This one penalises the right action. A pass that writes a human-lane test grows the bucket; a pass that writes a bogus command shrinks it. That gradient points away from the thing the ruleset asks for, and it points that way on every future pass, against an agent under a spend ceiling that is measured by how much outstanding work remains.

It also explains a number in the rollup that otherwise looks like neglect. Of the 65 solutions in that bucket, a large share have tests that name people as the measurement — "Five-minute orientation task on a static mock", "Test do operators get value with remote push off", "Hand-compute unblock counts and see if the operator's pick changes", and the whole commercial branch about pricing, cohorts and willingness to pay. Those are not un-instrumented through laziness. They are correctly un-instrumentable, and the bucket has no way to say so.

**What would fix this face specifically:** `solutionsMissingInstruments` should exclude a solution whose tests all carry a lane that puts them beyond compute — the same way the status filter proposed above excludes a solution that already shipped. The information is on the test's frontmatter already.

**And it compounds with a grant problem recorded elsewhere.** For a test created *before* this rule existed, the correct disposition is `ost_flag_humans_required`, which is denied on the unattended surface — twice now, in two independent firings. So the pre-existing human-lane tests cannot be labelled by the pass that finds them, and their solutions stay in this bucket permanently, where the only available action is to invent a command that cannot honestly measure them. See "The unattended run is scoped for tools nobody granted it, and it finds out one denial at a time".

_Observed directly on 2026-08-06: one `ost_create_node` call with `humansRequired`, one `ost_next_work` before and after, count 64 → 65._

## Issues
- 2026-08-06 2026-08-06, later firing — face 1's count corrected upward, and the direction matters. This node says "at least 5 of the 64 listed are `status: shipped`". A direct count over the vault finds **10** solutions carrying `status: shipped`, and every one of them is structurally unable to leave `solutionsMissingInstruments`: the five named here plus "Every self-observation channel names which of its sources each item came from", "Every count states the denominator it was taken over", "Every recorded step carries the directory and argv it actually ran with", "Flag a threshold that is still an instruction to choose one", and "The uncovered statement printed next to what the test asked for".

So the permanently-stuck floor under that bucket is at least 10 of 65, not 5 of 64, before counting the human-lane share described in face 3. The bucket's drainable fraction is smaller than any previous pass has recorded.

Not merged into the body above because it sharpens a number rather than adding a face, and the argument it sharpens is already made there correctly.

## Face 2, enumerated — so no future pass has to re-derive it

This node establishes that `underservedOpportunities` counts parent opportunities whose solution space lives on their children, and estimates "roughly half". The 2026-08-06 sweep's list of 26 has now been sorted item by item against the rollup's own bucket list. The split is worse than half:

**Bucket categories (15).** These are the Outcome's direct children — the filing layer the ruleset requires. Each carries a large subtree; each reports `solutions: 0, needed: 3`. Ideating directly beneath one would attach a specific solution to a category, which is the shape `outcome-files-categories` exists to prevent.

"A test that failed because the machine was busy looks exactly like one that failed because I broke something", "Building crowds out the search for better evidence", "Checking on progress means digging through files", "Don't want to buy a second AI credential just to try it", "I can't leave the process running unattended without worrying", "I can't say why anyone wouldn't just do this by hand with Claude and Obsidian", "I can't tell if anyone outside my own head wants this", "I have a tree full of unvalidated nodes and no idea which one to pick up", "I need the tree's output to be actionable by compute alone, because my hours don't exist", "I want my usage to automatically feed into and make the OST-Agent better", "The agent has to guess what resources it's actually working with", "The goal I care about is too far from anything I can act on this week", "The pass never says it is done, so I can't tell when to stop paying for compute", "Trust an unmonitored agent enough to walk away", "What the agent learns doesn't accumulate over time".

**Re-parented, documented, and still listed (1).** "The same refusal is rediscovered every session, because nothing carries the lesson forward" — the case this node already describes.

**Deferred and retired, and still listed (1).** "Want proof no hijackable capability even exists" carries `status: deferred` and the same sweep response reports it under `retiredFromDuplicateScan`. So one part of `ost_next_work` knows it is retired and another part is asking for a third solution beneath it. That is a **fourth face**, and it is the cheapest of all of them to fix: the exclusion the duplicate scan already applies is simply not applied to the underserved count.

**Genuine gaps (8).** Leaf needs with no solutions and no reason not to have them: "A second process is editing the same files, and a failed string match is the only notification", "I can't tell what a half-finished run actually finished", "Improving how the agent works means interrupting it", "The whole loop waits on one human command, and nobody is told it is waiting", "The work I most want to run unattended is the work that keeps needing a decision", "Two agents sharing my vault can trample each other", "Waiting on a slow external check burns the session, because every obvious way to wait is refused", "What the agent struggles with every session disappears".

**So 8 of 26 are real work and 18 are the bucket mis-reporting.** The pass that wrote this served two other genuine gaps to completion — "A guard derived the rule it was checking, so it agreed with the bug for 23 releases" and "Commands are composed against a repo layout nobody checked, so the first thing that runs is a path that isn't there" — and both left the list, which is the control that shows the remaining 18 are not merely un-worked.

_Sorted by hand against the rollup's bucket list on the 2026-08-06 sweep. Re-checkable by anyone comparing `ost_next_work`'s underserved list against the Outcome's direct children._

## Measured — the under-served queue is 25/26 already-settled work (unattended sweep, 2026-08-06)

This node says settled work comes back. This pass counted it on one specific queue, and the number is close to total.

`ost_next_work` reported **26 opportunities with fewer than 3 solutions**. Every one was checked:

- **15 of 26 are the rollup's own named buckets** — "Trust an unmonitored agent enough to walk away", "The agent has to guess what resources it's actually working with", "The pass never says it is done", and twelve more. These are category nodes whose job is to hold sub-opportunities, and the rollup shows their subtrees carrying 31, 45 and 15 solutions respectively. They report as under-served because they have no *direct* solution child.
- **1 of 26 is retired** — "Want proof no hijackable capability even exists", `status: deferred`, and the sweep's own response withholds it from the duplicate scan while still counting it here.
- **Of the remaining 10, nine were read in full this pass. Seven carry Opportunity children** and were made into categories deliberately: "The work I most want to run unattended…", "The whole loop waits on one human command…", "What the agent struggles with every session disappears", "The same refusal is rediscovered every session…", "I can't tell what a half-finished run actually finished", "Improving how the agent works means interrupting it", and "Two agents sharing my vault can trample each other".
- **Two are genuine unserved leaves**, and one of those two is a suspected near-duplicate of an existing node.

**The mechanism, stated so it can be fixed rather than re-noticed.** The under-served rule counts direct Solution children. Nesting a sub-opportunity under an opportunity is the tree's own prescribed way to grow the opportunity space, and doing it correctly moves that node's solutions one level down — after which the parent reports as under-served **permanently**, and no amount of correct work clears it. The 2026-08-05 pass's History lines are visible on several of these nodes doing exactly that re-parenting, and every node it touched is on this list.

**Why this is worse than noise.** The instruction a pass receives is to ideate up to the minimum. Followed literally against this queue, it would attach three solutions directly to fifteen category nodes — flattening the opportunity space the previous passes built, and putting solution nodes on the bucket layer the root's own invariant exists to keep clean. The queue does not merely waste attention; it asks for the opposite of the structure.

**What would settle it:** whether an opportunity with Opportunity children should count as under-served at all. If the answer is no, this queue drops from 26 to 3 and the pass's ideation budget goes to the leaves that actually lack candidates.

_Source: `ost_next_work` output of 2026-08-06 and direct reads of the nine node files named above. Observed behaviour of this product's own sweep. Corroboration only; the node's rung is unchanged._

## A measured census of one bucket, taken this pass (2026-08-26 unattended sweep, repo sight held)

This node argues the case in general. Here is the general case counted, on the largest bucket the sweep reports.

**Method.** `ost_next_work` listed 62 solutions under `solutionsMissingInstruments` (25 shown, the cap). This pass read 10 of the 25 in full — chosen for looking most mechanically instrumentable, so the sample is biased *towards* finding real work — and asked of each whether the missing instrument was an oversight.

**Result: 10 of 10 were correct declines, not omissions.** They sort into three kinds:

- **Six carried a prior pass's recorded reasoning already**, some of it years-of-passes deep: "Remote push optional and off by default" (already shipped and pinned by two green specs, verified first-party by the 2026-08-23 sweep); "Append-only tool surface with no delete or shell tool" (seven passes declined, with a standing ask to a human to choose between two dispositions); "Ship the helper with its own runtime rather than borrowing the machine's" (the mechanical half is owned by a sibling's test, so a second spec would measure one fact under two names); "Maintain a running per-item task list…" (the artefact is the harness's own task list, outside this repository); plus the two axiom candidates.
- **Two had never been examined and are genuinely people-shaped**, now annotated: "Show the whole write, exactly as it will land, and require a confirm before it does" (does seeing the bytes change a caller's mind) and "Scheduled ambient passes that page the operator only at hard gates" (two weeks must elapse, then a person judges the cost).
- **Two are positioning candidates whose own prose already names the human test**: "Ship it as something that grades a hand-built tree rather than replacing the hand" needs three hand-built vaults and their owners; "Name the specific mechanisms a hand process structurally cannot have" says outright that "that framing risk is the thing to test, not whether the mechanisms exist."

**What the number means.** On this sample the bucket's yield of real work is 0 of 10, and the two entries that yielded anything yielded an annotation rather than an instrument. Extrapolating the sampled rate, a firing that worked the bucket as a backlog would re-read something close to 62 nodes to produce nothing an instrument. That is not a defect in any of those nodes; every decline was right. It is exactly the cost this node names, with a denominator attached.

**The sharper form of the problem, visible only from inside the bucket.** A decline recorded in prose is invisible to the counter. `solutionsMissingInstruments` asks one question — does a test beneath this solution carry an `instrument:` field — and a node that answers "no, and here is 3KB of first-party reasoning for why no honest instrument exists" is indistinguishable from a node nobody has opened. So the tree's own accumulated judgement is unreadable by the surface that generates the work, and each pass either re-derives it or writes another copy of it. Six of the ten already carry between one and seven such copies.

**What would fix it, and it is not more annotation.** A disposition the counter can read — the evidence side already has the vocabulary (`withheldByDisposition` is a field in the sweep response, empty here) — so that "examined, no honest instrument exists, reason on the node" is a state, not a paragraph. Until then, every pass pays this and the honest thing is to say so in the report rather than churn.

_Method: first-party `ost_read_tree` reads of the ten named nodes this pass, plus `ost_next_work`'s own counts. Nothing executed, no test run, no result recorded. Grounds feasibility and cost; silent on desirability. Rung unchanged at the floor._

## The mechanism this node asks for has shipped — found first-party, 2026-08-28

The 2026-08-26 census above closes by saying what would fix this, and rules out the alternative: *"A disposition the counter can read — so that 'examined, no honest instrument exists, reason on the node' is a state, not a paragraph. Until then, every pass pays this."*

**That state exists in the product now.** `src/knowledge/suppressions.ts` is built, and its own docstring names this node's situation as the motivating case, in this node's own terms: *"Passes keep meeting items they correctly decline… Today the decline leaves nothing behind, so each pass pays the full reading cost to reach the answer the last one reached."*

**What it is, and why the design answers the objection this node would otherwise raise.** A suppression is not a deferral of the node — the node stays live, on disk, in the tree — it suppresses the *demand*, and it expires on a **fact rather than a date**. The condition vocabulary is closed and machine-evaluable against the tree alone, and prose is refused at the write funnel (`parseSuppressionCondition` throws `PROSE_REFUSAL`), on the stated grounds that *"an item suppressed on [a prose condition] is removed from the queue permanently by the writer's own say-so — that is a delete wearing a different name."* Revival is self-clearing: nothing marks a suppression expired, every read re-evaluates, and a damaged ledger line suppresses nothing, so corruption surfaces *more* work rather than less.

**Two of the four condition kinds were written for the exact faces this node enumerates:**

- `status-is` — face 1, the shipped solutions that structurally cannot leave `solutionsMissingInstruments`. The Issues note above counts at least 10.
- `lane-unlabelled` — face 3, and its docstring says so outright: *"An item declined because the surface lacked the tool to classify it."* That is the pre-existing human-lane tests which `ost_flag_humans_required` is withheld from labelling, described in this node's paragraph 57 as staying in the bucket "permanently".

**The read path is already wired into the sweep.** `suppressedByCondition` is a live field on the `ost_next_work` response — this pass received it, empty — alongside the `withheldByDisposition` field the census paragraph noted was empty. So the counter can already read the state; what is missing is entries.

**What this pass could NOT verify, stated so nobody takes it as confirmed.** Whether `ost-agent suppress` is actually exposed as a CLI command. `src/cli/index.ts` is 148,729 bytes — past the read cap — and this surface has no repository search, so the file could be neither read nor grepped. Two facts point opposite ways and neither settles it: the module's docstring asserts *"the write path ships on the CLI (a human's `ost-agent suppress`), not on any agent tool"*, while `test/cli/` contains `dispose.test.ts` and no `suppress.test.ts`, and `test/knowledge/` has no `suppressions.test.ts` either. A module with a wired read path, no CLI spec and no unit spec is consistent with "shipped and untested", with "half-built", and with "tested somewhere this pass did not look."

**So the actionable line for the operator, in descending order of confidence:**

1. Check whether `ost-agent suppress` runs. One invocation settles it.
2. If it does, the two counts this node has measured are drainable today without touching a node: the ≥10 `status: shipped` solutions under a `status-is` condition, and the human-lane tests under `lane-unlabelled`. Both revive by themselves if the fact flips.
3. If it does not, the missing half is small and precisely specified — the module, its vocabulary, its refusals and its disclosure format are all written; only the write command is absent.

**What does not change.** This is still a human's write by design, for the reason the module gives: the abuse it cannot police itself is *"a condition chosen because it will never flip"*, caught only by a person reading `formatSuppressions` over time. No pass can drain its own queue, and this pass did not try to. Recorded here rather than acted on.

_Method: first-party `ost_read_repo` reads of `src/knowledge/suppressions.ts` in full, plus directory listings of `src/cli`, `test/cli` and `test/knowledge`, and a size probe of `src/cli/index.ts`. Nothing executed, no test run, no result recorded. Grounds feasibility; silent on desirability. Rung unchanged at the floor._
