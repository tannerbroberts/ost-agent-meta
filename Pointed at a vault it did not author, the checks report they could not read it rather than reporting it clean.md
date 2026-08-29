---
type: Assumption
source: 'agent-run:unattended-sweep-2026-08-29'
created: '2026-08-29'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

**The belief, stated so it could be false.** The whole pitch above is "point the tool at the vault they already have and let it run the checks." That presupposes the checks *reach* a vault this tool did not author. If they cannot, the candidate does not merely underperform — it ships a grader that tells every hand-builder their tree is perfect, which is worse for them than no grader at all.

**Why this is in doubt, read off the code rather than guessed.** A hand-built Obsidian vault's notes carry no `type:` frontmatter, because nothing wrote them through this product. Three facts compose:

- `Vault.readTreeCensus` files a note with no frontmatter `type` under `skipped`, whose own definition is "enumerated, readable, but not an OST node" (`src/ost/census.ts`).
- `readTree()` returns only `nodes`. For a foreign vault that list is empty, so every invariant walks an empty set and returns zero violations.
- Zero violations over zero nodes is the exact sentence `src/ost/sweep.ts` was written to refuse: "a sweep that read nothing is a failure, not a clean run."

**The reason to think it is answerable rather than merely wrong.** The machinery already exists and is already correct — it is the wiring that is missing. `TreeCensus` carries `examined` and `skipped`, which is precisely the `offered`/`read` pair `SweepSubject` asks for, and `classifySubject` already returns `totally-blind` with `exitCode: 1` for `read === 0`. `sweep.ts`'s own docstring names the subject types it is for: "files in the directory, **nodes in the tree**, rows in the ledger." The tree-census consumer is the one named case with no spec behind it: the only wiring asserted anywhere is the search path, in `test/ost/unread-subject-propagation.test.ts`, which routes `searchSubjects(...).toSweepSubject()` into `sweepReport` and never touches the tree census.

**What makes this belief load-bearing rather than tidy.** This tree already holds the general failure as its own opportunity, "A sweep that cannot read its subject reports a clean result". This assumption is that failure pointed at the one population this candidate exists to serve — people whose vaults were never written by this tool, which is every prospect the pitch names. A grader that is silently blind on foreign vaults is not a weaker version of the product; it is a confident wrong answer delivered to strangers on first contact.

**What it deliberately does not claim.** Nothing here says the checks would produce *useful* findings on a foreign vault once they can read it. That is the sibling assumption already on this node, "Checks over a hand-built vault surface findings its owner did not already know", and it needs real vault owners. This one is the mechanical floor beneath it: the sibling cannot be true unless this one is, and this one being true does not make the sibling true.

**Provenance.** Composed by an unattended pass from first-party `ost_read_repo` reads of `src/ost/census.ts`, `src/ost/sweep.ts`, `src/ost/frontmatter.ts`, `src/ost/legacy-fallback.ts` and `test/ost/unread-subject-propagation.test.ts`, plus the `test/ost` file listing. Nothing was executed; the conclusion that no spec wires the tree census into `sweepReport` is drawn from a directory listing and the contents of the one file that does the equivalent wiring for search, so it is a strong inference rather than an exhaustive search. A reader with a shell should confirm by grepping for `toSweepSubject` and `sweepReport` callers before building.
