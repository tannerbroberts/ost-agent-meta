---
type: AssumptionTest
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
threshold: >-
  All three disposition kinds round-trip through one entry type, and every
  bucket's read path consults the ledger through one shared call. Any bucket
  needing its own entry kind or its own read fails it.
instrument: npx vitest run test/ost/disposition-ledger-shape.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** Write three dispositions — an evidence id acknowledged as corroborating an existing node, a solution recorded as shipped, an opportunity recorded as served by its children — then re-run `computeNextWork` and assert each item is absent from its bucket, with no per-kind branch in the read path.

**Why it is red today.** No such store exists on any surface. This is the weaker kind of red: the assertions describe a mechanism that is wholly absent rather than one that is present and wrong, so the spec fails first on the import. That is stated plainly because it matters for what the test is worth — it gives a builder a definition of done, but it is not a falsifiable prediction about behaviour that exists. The one thing it does pin, established by direct test on 2026-08-05 and recorded on "Evidence that fits no layer keeps coming back, so the pass never runs out of work", is the constraint the design must honour: a `## Disposition` section in a node body was tried and the sweep did not see it, so the ledger must live where the sweep reads, not where a reader reads.

**What a green run does not settle.** It proves one schema is sufficient — a feasibility question, and the cheapest of the ones this candidate raises. It says nothing about the risk that decides whether this should ship at all: that a disposition removes work by assertion rather than by anything checkable, written by the party whose budget the work costs. That is "An operator would accept a pass dismissing its own work list by written assertion", and it needs people.
