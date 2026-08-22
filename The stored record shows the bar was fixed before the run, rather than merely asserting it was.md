---
type: Assumption
source: 'agent-ideated:2026-08-22-unattended-sweep'
created: '2026-08-22'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[File a result dated before its own threshold and require the record to say so]]

**The belief, stated so it can be false.** The billable unit this solution defines is not "a test" — it is "a test run to a threshold committed *before* it ran". The word doing the pricing work is `pre-committed`, and it is the only part of the unit a customer cannot verify by looking at the deliverable. This node is the belief nobody wrote down: that the ordering is auditable from the stored record, so an invoice for ten pre-committed tests is a claim the vault can back rather than one the vendor makes.

**Why it is the mechanical half.** The sibling assumption, "Buyers value the design of a test, not just the running of it", is a buyer's belief and correctly a person's. This one is about what the files can prove, and a spec answers it.

**Grounds for doubting it, read from source this pass.** `src/ost/results.ts` is strict about attribution and about limits and silent about time. `recordResult` requires a verdict, a note, a `by` and an `uncovered` — each refused when blank, each with an argument in the code for why. Its date is `filing.on ?? new Date().toISOString().slice(0, 10)`: caller-supplied, defaulted to today, and compared against nothing. Nowhere does the filing path read the test's threshold, its `created:` date, or its History before writing the result line. So the record contains a bar and a result, and no evidence of their order.

Two things make that gap wider than it sounds rather than pedantic. The `threshold:` frontmatter field has no typed-transition tool — it is write-once at `ost_create_node` — so a change to it leaves none of the History trail that status, evidence, lane and instrument each leave. And the vault is deliberately plain Markdown a human is invited to open and edit, which is the property the neighbouring positioning solution *sells*; the same openness is what makes "the bar has not moved" unprovable from the file alone. Git holds the answer, and nothing in the product asks it.

**What turns on it.** Per-test pricing is the only one of the three pricing candidates whose unit contains a claim about the vendor's own conduct. If a customer cannot check it, the pricing model is asking to be trusted on exactly the point the product's whole positioning says not to trust anyone on — which is a worse position than charging for something duller.

⚠️ Unvalidated. Agent-ideated from a first-party read of `src/ost/results.ts` in full.
