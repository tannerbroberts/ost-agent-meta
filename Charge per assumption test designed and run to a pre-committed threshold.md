---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Buyers value the design of a test, not just the running of it]]
[[The stored record shows the bar was fixed before the run, rather than merely asserting it was]]

The unit is one tested assumption: the risky belief named, the test designed small and fast, the threshold committed before it runs, the result recorded with what it failed to cover. Priced per test. A customer who buys nothing gets nothing, and a customer who buys ten has ten things they know that they did not know before.

This prices the only step in the whole process that produces new knowledge. Mapping and ideation rearrange what is already believed; the test is where belief meets the world, and it is the part a customer can feel the absence of.

**Compared to the alternatives.** The clearest value story of the three and the easiest to justify to someone else's finance function, because each unit has a deliverable. It is also lumpy and unpredictable revenue, and it sits awkwardly against the tool's own hard rule that a human runs the test — so what is actually being sold is design and record-keeping, with the customer supplying the labour that makes it real. That is a harder thing to charge for than it sounds.

**What would make this the wrong pick.** Customers may see the test design as the cheap part and the running as the expensive part, in which case they are paying for the wrong half. Worth asking before pricing anything.

Whether anyone would pay this is a question for customers. Nothing here is validated.

## History
- 2026-08-05 unlinked "Ask ten buyers to split a test's price between designing it and running it" — moved under "Buyers value the design of a test, not just the running of it" — the belief this test measures now has a node of its own

## Definition of done

"File a result dated before its own threshold and require the record to say so"

```
npx vitest run test/ost/precommitment-ordering.test.ts
```

Bar: 0 of 20 filings whose run date precedes the threshold's commitment are accepted silently — each is refused or marked, naming both dates. At least 19 of 20 ordinary in-order filings are unaffected, because a check that fires on honest filings gets turned off.

**This is the feasibility half only.** Green makes an invoice for pre-committed tests checkable against the vault. It says nothing about whether anyone buys the unit — that is the assumption "Buyers value the design of a test, not just the running of it", and a person is the measurement.

The command is a `no-spec` red today. The mechanism it is red about is specific and was read this pass: `recordResult` in `src/ost/results.ts` computes its date as `filing.on ?? new Date()...` and never reads the node's threshold, `created:` date or History before appending. The comparison is absent, not lenient — there is nothing to tighten, only something to add.

**Worth a decision before building:** refuse the out-of-order filing, or file it with the discrepancy recorded beside it. Refusing is cleaner and loses a real result when a date was merely mistyped; marking keeps the result and puts the burden on the reader. Either satisfies the bar. The test exists to make that choice unavoidable, not to make it.
