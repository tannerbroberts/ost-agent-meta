---
type: Assumption
source: 'agent-run:unattended-sweep-2026-08-29'
created: '2026-08-29'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion
[[A closed solution disposition clears the instrument bucket entry and names it under withheldByDisposition]]

**Kind: feasibility.** The candidate's entire claim is that nothing needs building — `omitDisposed` already does the filtering and the disclosure in one call, `DISPOSITION_KINDS` already contains `"solution"`, and adoption is a single call site. If the instrument bucket cannot in fact be wired that way in one line — because its items are keyed by something other than the solution title, or because the disclosure channel is per-bucket and the instrument bucket has none — then this is not an adoption at all and its advantage over the siblings evaporates.

Stated so it could be wrong: filing a `closed` disposition of kind `solution` against a solution title removes that solution from `solutionsMissingInstruments`, and the same response names it under `withheldByDisposition`, with no new record type and no per-bucket special case.

The read this pass performed makes it plausible: the module's docstring names three faces it was designed for — an evidence id, a solution owing an assumption test, an opportunity's claim about its children — and the instrument bucket is not among them. That absence is the risk. It reads like a call site nobody added, but it could equally be an exclusion somebody chose.

**The half this cannot reach.** Whether the exclusion was deliberate is a question for whoever wrote it, and whether the operator would ever file such a disposition is a question about the operator — this vault has had a drainable evidence queue for weeks and zero live dispositions. A green here proves the wiring works and proves nothing about either.
