---
type: Assumption
created: '2026-08-18'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

Feasibility/desirability belief: if the file changed between the auto-read and the write actually landing, an invisible auto-read doesn't quietly paper over the same staleness the original guard was built to surface — it could turn a loud, safe failure into a silent, unsafe overwrite.

## Issues
- 2026-09-02 2026-09-02 unattended sweep — this assumption carries no AssumptionTest, and no bucket will ever ask for one. The parent solution's 2026-08-17 note already records that the test was not created. What is not recorded anywhere is why nothing has chased it since: the sweep counts assumptions per SOLUTION, never tests per ASSUMPTION. `solutionsMissingAssumptions` asks only "does this solution have at least one assumption" and is empty this firing; `solutionsMissingInstruments` asks only "does this solution have at least one instrumented test" and lists the parent for the other reason. So a solution can satisfy both counters while one of its beliefs is wholly untested, which is the distinction the Assumption layer was added to keep — a solution resting on several beliefs is not covered by one test against one of them. Observed on this node: the parent has two assumptions, the sibling carries the only test, and this one is invisible to every bucket the sweep emits. Scale, bounded rather than asserted: node files carrying no child wikilink number about 502 against 506 AssumptionTests, so childless assumptions across the whole tree are on the order of a handful, not hundreds — the gap is real and its current incidence is near zero. Limits: the bucket definitions are read off this firing's own `ost_next_work` response and the tool's description, not off `src/mcp/next-work.ts`, which is 99KB and would truncate; `ost_check` is withheld on this surface, so whether an invariant covers this could not be tested directly — the only evidence against it is that `hygieneIssues` is 0 this firing while this node sits untested. What a human might do: decide whether an assumption with no test deserves a counter of its own, and either write this one's test or record that the belief is settled by the parent's 2026-08-22 repo-read finding, which argues the feasibility half from `src/git/read-write-hash-guard.ts` without ever testing it.
