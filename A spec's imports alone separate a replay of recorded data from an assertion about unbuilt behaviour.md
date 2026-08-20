---
type: Assumption
source: 'agent-ideation:2026-08-20-unattended-sweep'
created: '2026-08-20'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[An import-only classifier labels the known replay spec replay and none of ten permit specs replay]]

**Kind: feasibility.** If the kind has to be declared by hand in frontmatter, the solution degrades to a convention a discovery pass may forget, and a forgotten declaration is indistinguishable from a permit spec — the failure it exists to fix. The claim worth testing is the stronger one: that the spec file itself says which kind it is, by what it imports. A replay spec imports a recorded-sessions fixture or reads the transcript store; a permit spec imports the module it expects to exist. `src/loop/question-stop-independence-replay.test.ts` (present in `test/loop/` this pass) is the one known replay-style spec in the suite, against which the heuristic can be checked, and every other spec in `test/ost/` should classify as permit.

**Stated so it could be false:** a classifier reading only import statements labels the known replay spec `replay` and labels none of ten sampled permit specs `replay`.

**What would change if it were false.** The kind becomes a declared field on the test node (`ost_set_instrument` would take it), and the vacuous-red problem gets a cousin: a replay spec filed as a permit because nobody declared it.
