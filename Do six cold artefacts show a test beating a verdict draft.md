---
type: AssumptionTest
status: unvalidated
source: >-
  agent-ideation:autonomous-loop-2026-07-25 — cheapest disconfirmer for the
  leave-a-test-behind candidate
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/runner/verdict-leaves-spec.test.ts
---
#AssumptionTest #unvalidated #desirability #evidence/assertion

**Assumption under test (desirability).** That an operator gets materially more from a committed test than from a verdict draft covering the same finding — enough more to justify compute spending longer on the harder artefact.

**Why this is the riskiest thing the parent rests on.** The parent candidate's whole argument is about *tomorrow*: both artefacts answer today's question identically, and the test is claimed to be worth more because it does not decay. That is an argument nobody has checked against a person. It is also exactly the kind of argument an agent finds appealing — writing tests is work compute is good at, and "it compounds" is unfalsifiable if never asked. If the drafts turn out to be just as useful, the parent is decoration and the lane triage alone is enough.

**Proposed test.** Take three compute-only-shaped items from the existing backlog that plausibly have an executable form. Have compute produce **both** artefacts for each — a verdict draft and a test — six artefacts total. Put them in front of the operator cold, without labelling which is which kind or which the agent prefers.

**Pre-commit the threshold before looking.** The parent survives only if the operator picks the test over the draft in **at least 2 of the 3 pairs** *and* can say what the test gives them that the draft does not, in their own words, without being prompted with the word "decay". A preference with no reason behind it is a preference for the thing that looks like more effort, which is not the claim.

**What would kill it outright.** The operator preferring the draft in 2 of 3, or preferring the test only because it looks more thorough. Either result should retire the parent and leave "Triage every assumption test by the human-minutes it actually needs, and let compute run the zero-minute lane" as the sole answer under this opportunity.

**Lane — deliberately unset, and that is the point.** Producing the six artefacts is compute-only. Reading them and choosing is irreducibly the operator, so the test as a whole is not. It is the first case in this vault where a *single* test spans two lanes, which the v0.6.0 model does not represent: a lane is a property of a test, and this test wants two. Whoever classifies it should either split it or record that the model is too coarse — the second would be a more useful finding than this test's own result.

⚠️ Proposed only — the agent does not run tests or record results.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/runner/verdict-leaves-spec.test.ts — There are no artefacts to hand six cold readers, because a verdict currently leaves a draft and nothing else — the comparison the test wants has only one side of it. This asserts the missing side: completing a verdict writes a committed spec file into the repository's own suite, that file is referenced by the test node it settled, and a verdict that produces only prose is refused. Missing-spec red, not assertion red — verdicts do not emit specs, so the command fails on a missing file; a builder should write it against the real verdict path so it goes red on a prose-only verdict that today succeeds. It does not settle the comparison itself: whether six cold readers find the test more useful than the draft is a person's reaction and stays with a human.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/runner/verdict-leaves-spec.test.ts` — No test files found, exiting with code 1
