---
type: Solution
source: 'agent-run:unattended-sweep-2026-08-29'
created: '2026-08-29'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[A closed solution-kind disposition takes a solution off the instrument bucket and is disclosed on the response that withheld it]]

**Variation dimension: bought-vs-built. Position taken: adopt what already ships, unchanged, and build nothing new.**

The parking mechanism this need asks for exists and is running. `src/knowledge/dispositions.ts` is an append-only attributed ledger whose `DISPOSITION_KINDS` already includes `"solution"`, whose `omitDisposed` does the filtering and the disclosure in one call so there is "no version of 'consulted the ledger' that quietly skips the second half", and whose every entry is reversible by a `reopened` line. Its own docstring says every work bucket looks at it before listing anything. The adoption is one `omitDisposed` call in the instrument bucket, passing the solution title as the subject and `"solutionsMissingInstruments"` as the list name.

**What is bought and what is built.** Bought: the record format, the attribution and reason requirements, the append-only reversal, the `Withheld` disclosure carried on the response that withheld the item, the audit command, and the deliberate placement of the write on a human's CLI rather than the agent's surface. Built here: nothing but the call site.

**Why the mechanism may not already cover this bucket.** The docstring enumerates three faces it was designed for — the evidence id, "a solution that shipped still owes an assumption test", and an opportunity's claim about its own children. The instrument bucket is not among them. Whether that is a missing call site or a deliberate exclusion is the thing to check first, and it is checkable by reading one file rather than by asking anyone.

**Contrast with the siblings.** The humans-required sibling adds a new agent capability; the two-counts sibling adds a new report shape. This candidate adds neither — it argues the product already solved this problem once and should not solve it twice, which is also its main risk: if the instrument bucket was excluded on purpose, adopting the ledger here overrides a decision without finding out what it was.

**What it does not fix, and this is the same limit the evidence face hit.** `dispose` is a human's CLI command by design, and this vault has zero live dispositions after weeks of the evidence queue being drainable by exactly this route. Wiring a second bucket into a ledger nobody writes to changes the count by nothing. The parent's need is met only if the operator actually files, which is a fact about the operator and not about the code.

⚠️ Unvalidated, agent-ideated. Grounded in a read of the shipped module this pass performed; no operator has said they would file dispositions against solutions.

## Definition of done

"A closed solution disposition clears the instrument bucket entry and names it under withheldByDisposition"

```
npx vitest run test/evidence/dispose-solution-instrument-bucket.test.ts
```

The spec does not exist yet, so this is `no-spec` today rather than assertion-red. `test/evidence/corroborate-disposition.test.ts` is the shipped template for the same contract on the evidence face — copy its shape. Four assertions, listed on the test node: three disposed solutions leave `solutionsMissingInstruments`; all three are named under `withheldByDisposition`; the node files are byte-identical afterwards; and a `reopened` entry puts all three back.

If the build turns out to need more than one `omitDisposed` call site, this candidate has lost the property it was ideated for — adoption rather than construction — and the comparison against its siblings should be re-run rather than the build continued.
