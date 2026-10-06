---
type: AssumptionTest
source: >-
  repo-read:2026-10-06-unattended-sweep — src/adapters/inbox.ts and
  test/adapters/inbox.test.ts, read first-party
created: '2026-10-06'
evidence: assertion
threshold: >-
  3 of 3 cases pass: a channel with a declared cadence whose newest file is
  older than it reports overdue; the same channel with a file inside the cadence
  reports 0 new and no overdue; a configured folder that no longer exists
  reports unreadable, not 0 new
instrument: npx vitest run test/adapters/inbox-cadence.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Kind: feasibility.** This tests the second clause of the parent assumption: whether the vault can tell an export that stopped from an experiment that produced nothing. The first clause, that an external export keeps arriving at all, is "Set up one scheduled export and check every week whether it is still arriving". That one is about someone else's scheduler and stays with a person. The 2026-09-02 sweep note on that test asked for this split, and this node is it.

**Lane: compute-only.**

**What the repository does today, read first-party.** `InboxSource.fetchSince` in `src/adapters/inbox.ts` has no notion of expected arrival. Nothing new reads as `items: []`, and so does a configured folder that has vanished: `if (!fs.existsSync(this.dir)) return { items: [], cursor };`. The existing suite pins that behaviour in place: `test/adapters/inbox.test.ts` asserts "missing inbox directory yields no items". So a sync mount that expired, a renamed export folder, or a producer that just stopped all report exactly what a quiet week reports. That is the failure the parent solution fears, and it can be seen in the code without waiting eight weeks.

**What the spec asserts.** A channel declares an expected cadence (for example `expectEvery: 7d` on the channel in `ost.config.yaml`, resolved by `resolveChannels`). Three cases, using the same `mkdtemp` fixture `inbox.test.ts` uses:
1. The newest file's mtime is older than the cadence. The fetch result, or the channel line `ost_ingest_inbox` prints, says **overdue** and names the age.
2. A file arrived inside the cadence. The result is 0 new and not overdue (non-vacuity: overdue is not always on).
3. The configured folder does not exist. The result says **unreadable**, not 0 new. A builder has to reconcile this with the existing "missing inbox directory yields no items" assertion, either by changing it or by limiting it to channels with no declared cadence. That choice is part of the deliverable.

**Which kind of red this is, said plainly.** The spec file does not exist yet, so today the command fails as **no-spec**. That is the weak kind of red, and it gives no build permit until the spec exists and fails on an assertion. What makes it worth more than a reserved filename: the mechanism that must change (`fetchSince`'s missing-dir branch, and a cadence field the channel config does not have) and the assertion that currently encodes the wrong answer are both named above. Writing the three cases against today's code would fail on assertions 1 and 3, not on a missing import of anything except the new config field.

**What a green does not settle.** It shows the vault can *notice* a stopped export. It does not show that any external export keeps arriving, that a person reads the overdue line, or that anyone wants experiment data carried this way at all. Desirability and viability stay where they were.
