---
type: AssumptionTest
source: 'agent-ideated:2026-08-03-unattended-sweep-builder-capability'
created: '2026-08-03'
evidence: assertion
threshold: >-
  Over two weeks, at least half of the collaborators offered the prompt deposit
  at least once, AND at least one deposits again without being prompted. Zero
  unprompted second deposits kills the candidate.
instrument: npx vitest run test/adapters/deposit-prompt.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**The assumption under test (desirability):** that people holding the reasoning will actually part with it when the channel is put in front of them. The opportunity asserts they would deposit if they knew it was welcome. That is a claim about willingness, and willingness is the one thing this candidate cannot route around — every other risk it carries is downstream of someone choosing to answer.

**The test:** for two weeks, close every session, PR and review with one question asking for the reasoning behind the work. Count two things separately: how many collaborators deposit at all, and how many deposit a second time without being asked. The second number is the one that matters — a first deposit measures politeness, a second measures whether the act felt worth it.

**Pre-committed before running, so this can come out a failure:** at least half of those offered must deposit at least once, and at least one must return unprompted. Meeting the first bar but not the second is a failure, not a partial pass — it is the signature of compliance decaying into paperwork, which is this candidate's stated decay mode. Zero unprompted second deposits kills it.

**Why it needs people by construction:** the measurement *is* what a human chooses to do when asked, and there is no artifact, replay or simulation that substitutes for it. No compute-only version of this test exists.

**A population problem worth stating before anyone runs it:** this vault currently has one human operator and no external collaborators, so "half of those offered" is a bar over an n that may be one. Run as-is it would measure the founder's own willingness, which is not the population the claim is about. A human should decide whether to hold this test until collaborators exist rather than run it against n=1 and record a number that reads stronger than it is.

**What it deliberately does not cover:** whether what gets deposited is accurate. Self-reported reach is not measured reach, and this test counts deposits, not truth.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/adapters/deposit-prompt.test.ts — Asserts the containment the node stakes its honesty on: the collaborator's answer is stored verbatim, nothing is inferred from it, and the evidence it produces enters at the assertion floor and cannot be promoted by the deposit path itself. Red today because no deposit channel exists in any adapter.
