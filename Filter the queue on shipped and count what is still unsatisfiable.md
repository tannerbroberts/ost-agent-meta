---
type: AssumptionTest
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
threshold: >-
  No solution with status `shipped` appears in `solutionsMissingInstruments`,
  and of the entries that remain, at most 10% are ones no spec file could ever
  settle.
instrument: npx vitest run test/ost/instrument-queue-excludes-shipped.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.**

**What this measures.** Build a fixture tree carrying solutions in each status, including shipped ones with prose-only tests and market-shaped ones whose claims are about pricing rather than mechanism. Run `computeNextWork` over it. Assert two things: no `shipped` solution appears in `solutionsMissingInstruments`, and the entries that survive are ones a spec file could actually settle.

**The bar, pre-committed.** Zero shipped solutions in the queue, and at most 10% of the remainder unsatisfiable-by-any-spec. The second half is the real test: it is what tells the difference between fixing a fifth of the problem and fixing it.

**Why it is red today.** The exclusion does not exist. This pass read the live queue and found "A result must state what it did not cover", "Post-session transcript harvester", "Refuse a proving command whose exit code cannot report failure", "Refuse a wiki-link that contains a newline" and "Refuse a write whose content is empty or literally undefined" in it, and grepped the vault to confirm all five carry `status: shipped`. A spec asserting their absence fails against today's code for the strongest available reason: the behaviour is observably not there, not merely unimplemented in a file nobody has written.

**What a green run does NOT settle.** It says the queue no longer lists shipped work. It says nothing about whether `status: shipped` was set truthfully — that field is written from prose by a human or an agent and is verified against the repository by nothing, so a solution marked shipped in error vanishes from the queue silently and this test passes anyway. It also says nothing about whether the operator wanted a draining queue rather than a queue that asks shipped work for something else; that is desirability and no spec touches it.
