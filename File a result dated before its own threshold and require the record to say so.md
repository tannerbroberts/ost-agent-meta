---
type: AssumptionTest
source: 'agent-ideated:2026-08-22-unattended-sweep'
created: '2026-08-22'
evidence: assertion
threshold: >-
  0 of 20 filings whose run date precedes the threshold's commitment are
  accepted silently; each is refused or marked, naming both dates. At least 19
  of 20 ordinary filings are unaffected
instrument: npx vitest run test/ost/precommitment-ordering.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**Pre-committed threshold:** 0 of 20 out-of-order filings are accepted silently — each is refused or marked on the record, naming the run date and the commitment date. At least 19 of 20 ordinary in-order filings go through untouched, because a check that fires on honest filings would be turned off within a week.

**What the spec does.** Build a fixture test node whose threshold was committed on a known date, then file results across the boundary. A result dated after the commitment files as it does today. A result dated before it — the case `recordResult` currently accepts without looking — must not land as an ordinary line. Both controls matter and the second is the one that carries the file: the 19-of-20 arm is what separates a working check from a check that refuses everything, and a spec without it would pass against a filing path that had simply been broken.

The second arm is the design question the assertion forces someone to answer, and it should be answered in the spec rather than in prose: refuse the filing outright, or file it with the discrepancy recorded beside it. Refusing is cleaner and loses a real result when a date was merely typed wrong; marking keeps the result and puts the burden on the reader. Either satisfies the bar. Neither is chosen here, because it is a product decision and this test exists to make it unavoidable rather than to make it.

**Why it is red today.** `test/ost/precommitment-ordering.test.ts` does not exist, so this is a `no-spec` red and is declared as one; the bound threshold is what keeps it a working permit. The mechanism it would be red *about* was read this pass and is specific: `recordResult` in `src/ost/results.ts` computes `const on = filing.on ?? new Date().toISOString().slice(0, 10)` and never reads the node's threshold, `created:` date or History before appending. There is nothing to disable and nothing to make stricter — the comparison is absent, not lenient.

**What this does NOT settle.** Everything about whether the unit sells. A green here proves an invoice for pre-committed tests is checkable against the vault; it says nothing about whether a buyer values test design over test running, which is the sibling assumption "Buyers value the design of a test, not just the running of it" and is a person's. It also does not make the *content* of a threshold honest — a bar can be fixed early and still be trivially clearable, which is a different defect this tree already tracks under thresholds that state no fixed bar.

⚠️ Unvalidated. Agent-designed; nobody has run it.
