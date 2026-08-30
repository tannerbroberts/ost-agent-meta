---
type: AssumptionTest
source: 'agent-ideation:2026-08-30-unattended-sweep'
created: '2026-08-30'
evidence: assertion
threshold: '>= 20 of 20 uncited repeats collapse, and zero novel singletons collapse'
instrument: npx vitest run test/evidence/uncited-repeat-collapse.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.**

**The assertions, written out so the deliverable is the spec and not the filename.** Clone the fixture in `test/evidence/age-out-preserves-novel.test.ts` with exactly one change: drop the `createNode`/`linkNodes` pair that makes `MAPPED_ID` a cited source, so the twenty redundant records share a body signature with *each other* and with nothing any node cites. Keep every other property of that file's first case — one identical timestamp across all twenty-one records, so pure age cannot pass, and the novel singleton `NOVEL_ID` present exactly once. Then, with `AGE_OUT_DAYS` passed to `computeNextWork`:

- `expect(work.agedOutEvidence).toEqual({ count: 20, oldest: OLD })` — this is the assertion that fails today, returning `{ count: 0, oldest: null }`.
- none of `REDUNDANT_IDS` appear in `work.unmappedEvidence`;
- `NOVEL_ID` does appear — the novelty guard, carried over unchanged;
- all twenty-two records remain on disk.

**Which of the two reds this is, stated plainly: the weak one, and not by choice.** The command names a spec file that does not exist yet, so today it fails as `no-spec` — the reason that would be identical for any question written on it. The strong form, naming the existing `age-out-preserves-novel.test.ts` with a `-t` filter selecting a new case, was composed first and **refused at the tool boundary**: `ost_create_node` accepts only the grammar `npx vitest run <path>.test.ts`, rejecting both a quoted `-t` (as shell punctuation) and an unquoted single-token `-t` (as not an instrument form). So on this surface an instrument can be red-because-specific only if some already-committed spec file is already failing; against a green suite, every writable instrument is red-because-absent. That constraint is worth a human's attention, because this tree's own records show 260 of 266 reds reading "No test files found" — this is a mechanism that would produce exactly that, and it is not agent laziness.

**Why the underlying question is still specific even though the command is not.** The failing assertion is named above and is about this predicate and no other: the implemented redundancy half requires a node citation, and the fixture removes it. Whoever writes the file has a definition of done that is one `toEqual` line, not "create this file."

**What it does not settle.** A green proves the predicate can be widened without the novelty guard letting a one-off through. It proves nothing about whether this vault's 463 real records share signatures with each other — the fixture supplies its own repeats by construction, and that census is the open question this branch inherits. It says nothing about what `evidence.ageOutDays` should be, whether an operator wants a shorter queue, or how the two sibling candidates compare. Feasibility answered mechanically leaves desirability, viability and usability exactly where they were.

Unvalidated. Agent-proposed 2026-08-30; not run, and no result is recorded.
