---
type: Solution
source: 'agent-ideation:2026-08-30-unattended-sweep'
created: '2026-08-30'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion

**Variation dimension: bought-vs-built. Position taken: adopt the existing mechanism whole and build only the one predicate it is missing.**

Nothing new is designed here. The collapse machinery already exists in this repository, is already specified, and is already safe — it is simply unreachable for the records that make up this queue.

**What is adopted as-is, read first-party this pass from `test/evidence/age-out-preserves-novel.test.ts`.** The age-out rule, its standing-backlog line (`agedOutEvidence` keeps the true count and the oldest timestamp rather than silently dropping), its guarantee that nothing is deleted from disk, and — most importantly — its novelty guard. The spec's header states the rule in capitals: **age alone may never collapse an item.** Its fixture gives all twenty-one records one identical timestamp so that pure age fails the test, and the equally-old novel singleton is asserted to survive. That guard is the hard part of this problem and it is already built and pinned.

**What is built here, and it is one predicate.** The rule as implemented is *old* **and** *redundant with a signature some node has already cited*. In the fixture, `MAPPED_ID` is redundant-eligible precisely because an Opportunity was created citing it. The records filling this vault's queue have no such citation and never will — as the sibling suppression branch argues at length, there is no genuine need underneath a self-manufactured record to distil, so no node ever cites one, and the 88% that do carry real errors go uncited because they repeat problems already on the tree. **So enabling `evidence.ageOutDays` today would leave exactly these records individually listed forever.** The build is to widen the redundancy half: a signature seen N times *within the evidence store itself* counts as redundant, independent of whether any node cites it.

**Against its siblings.** This is the only candidate that reduces what is stored and listed rather than only how it is read, and the only one that asks no person for anything on an ongoing basis. It buys the novelty guard for free, which neither sibling has at all — the read-time grouping can merge two different problems invisibly, and the curated list is only as good as the last time someone looked at it.

**What it gives up, plainly.** It collapses on age *and* redundancy, so a brand-new instance of a long-standing problem waits out the whole window before it can fold — the queue stays noisy for `ageOutDays` after every recurrence. It inherits a knob (`evidence.ageOutDays`) that is unset on this vault and that nobody has yet argued a value for. And widening a predicate that currently keys on "a human found this worth citing" to key on "this repeats" removes a human judgement from the loop, which is the opposite of what the curated sibling does deliberately — if the frequency threshold is wrong, a novel-but-repeating problem gets buried by machinery nobody inspected. That risk is exactly what the novelty guard was written to catch, which is the argument for extending this spec rather than writing a new mechanism beside it.

**Honest note on how this was ideated.** All three candidates under this opportunity were composed in one context by one author, because this surface holds no grant to run independent parallel ideators. Discount their apparent distinctness accordingly.

Unvalidated. Agent-ideated 2026-08-30; a human to review.
