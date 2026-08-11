---
type: AssumptionTest
source: 'INBOX:2026-08-10-founder-theory-simulated-dissent-as-counterparty.md'
created: '2026-08-11'
evidence: assertion
threshold: >-
  Panel rejects at least 9 of 10 planted-defective instruments including every
  vacuous-red canary, accepts at least 4 of 5 valid ones, and recorded dissent
  rate is nonzero across the run.
instrument: npx vitest run test/eval/dissent-canary-catch-rate.test.ts
---
#AssumptionTest #machine-witness #goal-acquisition #unvalidated #evidence/assertion

One small, fast test of one belief: that a persona-diverse dissent panel reliably rejects invalid instruments, and that its reliability is measurable by machine.

**Design.** Build a canary corpus of planted-defective instruments — vacuous reds (the vault's own 260/266 "No test files found" episode is the first canary class), tautological passes, and mis-scoped specs — mixed with valid instruments. Run the panel over the corpus with pass semantics frozen before the run. Measure three things: catch rate on the defective set, false-rejection rate on the valid set, and dissent rate across the debate (a panel that never disagrees is declared dead regardless of its verdicts).

**What the spec asserts.** `test/eval/dissent-canary-catch-rate.test.ts` constructs the corpus as fixtures, invokes the panel, and asserts the three measurements against the threshold. It is red today because neither the panel nor the spec exists — a `no-spec` red, which grants nothing; the deliverable is the failing spec, created through the normal branch/PR flow so main stays green, and this test is not finished until that spec exists and fails on an assertion rather than on a missing file.

**What a green would NOT settle.** A passing panel proves the shallow canary classes are catchable. It says nothing about the three substrate risks named on the parent assumption — shared blind spots below the prompt layer, orchestrator capture, and dissent collapse against novel (non-canary) defect classes — and nothing about whether anyone wants machine-cleared permits at all. Feasibility answered here leaves desirability, viability and usability exactly where they were.
