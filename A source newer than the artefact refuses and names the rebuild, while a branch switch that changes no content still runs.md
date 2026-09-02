---
type: AssumptionTest
source: 'agent-ideation:2026-09-02-unattended-sweep'
created: '2026-09-02'
evidence: assertion
threshold: >-
  All 4 cases pass: both stale cases exit non-zero naming the rebuild command,
  and both no-content-change cases exit 0; 0 of the 4 may run the build.
instrument: npx vitest run test/cli/stale-artefact-refusal.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

Four cases over a fixture checkout, chosen so the two failure directions are separated rather than averaged.

**The two that must refuse.** A source file edited after the artefact was written. A source file added after the artefact was written. Each must exit non-zero, print the rebuild command by name, and leave the artefact untouched — the refusal must not repair, because the parent candidate's whole position is that the repair stays manual.

**The two that must not refuse.** A checkout that touches every source mtime without changing any content. A source edited and reverted to its original bytes. Each must exit 0 and run normally. These are the cases that decide whether this candidate is usable at all: the first is the ordinary shared-checkout churn this repository's firings actually live in, and it is where a naive mtime comparison fails.

**Pre-committed bar, fixed before anything runs.** All four, and zero of the four may invoke the build. Three of four is a fail: passing both refuse cases and one no-change case is exactly the shape of a checker that blocks a firing for nothing, which the parent assumption says is worse than the crash it replaces.

**Instrument honesty, stated rather than hidden.** `test/cli/stale-artefact-refusal.test.ts` does not exist, so the first run is filed `no-spec` and grants no build permit. That is a grammar limit rather than a choice — `ost_set_instrument` accepts only a bare `npx vitest run <path>.test.ts` and refuses the `-t` filter that would let an assertion-level red be expressed inside an existing spec. The path sits in `test/cli/`, an existing directory, and the four cases above are named precisely so the builder writes assertions rather than inventing a question.

**What a green here does not settle.** It measures the predicate, not the product. It says nothing about whether an operator wants to be blocked rather than warned — the tree already carries "Ask the operator whether they'd rather a warning let the write through than have it hard-blocked" for that, and it is a human's answer. It says nothing about the cost of running the check ahead of six sequential CLI invocations, and nothing about desirability or viability: a checker that is accurate is still a checker nobody asked for.

⚠️ Proposed only — the agent does not run tests or record results.
