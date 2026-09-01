---
type: AssumptionTest
source: 'agent-ideation:2026-09-01-unattended-sweep'
created: '2026-09-01'
evidence: assertion
threshold: >-
  exactly 0 queue entries created via the humansRequired argument report
  ageDays: null
instrument: npx vitest run test/ost/ask-clock-at-creation.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

Create an AssumptionTest through the `humansRequired:` creation argument rather than through `flagHumansRequired`, then read the queue from a fresh context over the same vault, clock-injected as the existing spec does. Assert the entry is present **and** that `ageDays` is a number.

Run against today's code this fails, and the way it fails is the finding: `ageDays: null` means the creation door writes no ask and the parent assumption holds; a number means the assumption is refuted and the sibling repair is aimed at the wrong path.

**The spec to write, precisely.** Copy the fixture from `test/ost/pending-ask-queue.test.ts` — `initVault`, `buildPassContext`, the same clock injection via `daysLater`, since an assertion about days waiting cannot race the wall clock. Change one thing: create the AssumptionTest with the `humansRequired` argument on the creation call instead of calling `flagHumansRequired` afterwards. Then `computeNextWork(buildPassContext(dir).vault, dir, 3, daysLater(11))` and assert `entry.ageDays` is `11`, not `null`.

**Why this instrument is red today, stated honestly rather than flatteringly.** `test/ost/ask-clock-at-creation.test.ts` does not exist, so this is a `no-spec` red: it fails for the reason *any* question written on that path would fail, it mints no build permit, and this test is not finished until the file exists and an assertion inside it fails. That is a real weakness and it is not the form this node wanted. The instrument surface accepts one bare spec-file command and refuses shell punctuation, so the stronger form — naming the existing `pending-ask-queue.test.ts` with a `-t` filter on the missing assertion — is not expressible here. A builder should treat the paragraph above as the actual definition of done and the filename as the address it goes to; a reviewer should not read a red on this command as evidence of anything until the file is written.

**What this does not settle.** Only the mechanical half. It locates where the ageless entries come from and whether the door can be closed. It says nothing about whether a dated ask gets answered sooner than an undated one — that is desirability, it belongs to a person, and a green here is a builder's definition of done rather than evidence that the queue works for its reader.
