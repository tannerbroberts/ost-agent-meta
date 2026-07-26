---
type: AssumptionTest
source: 'agent-ideation:2026-07-26-tenth-pass'
created: '2026-07-26'
evidence: assertion
---
#AssumptionTest #evidence/assertion

**The single assumption.** That a marker distinguishing machine-selected text from human-written text keeps carrying information after it appears on nearly every line — rather than becoming furniture, as this vault's own markers arguably have.

**The evidence already on file, and it is not encouraging.** 212 of 219 nodes in this vault carry `evidence: assertion`, and `#unvalidated` sits on 211 of them. A marker that is true of ~97% of what a reader sees cannot be doing much discriminating. This test exists because the proposed solution is the same move at a finer grain, and the coarse version has already had this happen to it.

**Lane: humans-required.** Whether a marker is *read* is a fact about readers.

**Pre-committed threshold.** Show operators two mixed outputs and ask them to point out which parts the machine chose. The marker works if **at least 4 of 6** identify machine-selected excerpts correctly **and** at least half of those mention the marker unprompted when asked how they could tell. Correct identification without a single unprompted mention of the marker counts as a **refutation**, not a pass — it means they used the content, and the marker is doing nothing.

**Cheaper precondition, which should be run first and needs nobody.** Count the fraction of lines in a representative `lanes`/`check`/`debt` output that would carry the marker. **If it is above 90%, do not run the human test** — the coarse-marker precedent above already says what happens, and spending five operators to re-learn it is waste.

⚠️ Proposed only — the agent does not run tests or record results.
