---
type: AssumptionTest
source: 'agent-ideation:2026-07-26-tenth-pass'
created: '2026-07-26'
evidence: assertion
---
#AssumptionTest #evidence/assertion

**The single assumption.** That the fourteen `undefined` lines are the *whole* population of silent bad writes — and not the one shape that happens to be greppable, with others (empty annotations, truncated bodies, lines that landed on the wrong node) sitting unnoticed beside them.

**Why the assumption matters more than the fix.** v0.17.0 closes the path that produced these fourteen. If the fourteen are the population, the defect is finished. If they are the visible tail of a wider habit of unchecked writes, then closing one path is a partial fix presented as a complete one — and this tree has just spent eight passes learning what carrying an unexamined conclusion forward costs.

**Proposed test.** Replay both vaults' full git histories. For every commit that added a line under `## History` or `## Issues`, classify the appended content: non-empty and meaningful, literally `undefined`/`null`, empty or whitespace-only, or truncated mid-sentence. Report counts per shape, per vault, per date, with the commit that introduced each.

**Lane: compute-only.** Two local git histories and a classifier. No credential, no outside person, nothing written to either tree.

**Pre-committed threshold, fixed before the sweep runs.** The "fourteen is the population" claim survives if the sweep finds **no more than 2** additional bad writes of any *other* shape across both vaults. **Three or more of a shape other than `undefined` refutes it**, and the write-level guard stops being a tripwire for one known bug and becomes the primary fix. Truncated-mid-sentence is judged conservatively: only a line ending without terminal punctuation *and* shorter than 40 characters counts, because prose legitimately wraps.

**What this cannot tell anyone.** Nothing about writes that were well-formed and *wrong* — a correct-looking annotation on the wrong node is invisible to every check proposed here, and would be the genuinely alarming shape.

⚠️ Proposed only — the agent does not run tests or record results.

## Issues
- 2026-07-27 RUN BY COMPUTE, 2026-07-27 (eleventh pass, autonomous loop). This is an agent-run compute-only measurement, NOT a human-recorded result — the test node stays unvalidated and no rung was raised.

Replayed all 106 commits across both vaults (ost-agent-meta 50, tetrix-ost 56) and classified every annotation entry ADDED under a History or Issues heading — 306 entries total (233 meta, 73 tetrix). Counts by shape: **21 literally undefined, 0 empty/whitespace, 0 truncated-mid-sentence.** Per-vault: 6 in ost-agent-meta, 15 in tetrix-ost, across 16 nodes.

The pre-committed threshold was: the claim survives if no more than 2 additional bad writes of any OTHER shape appear; 3 or more refutes. Zero of any other shape were found, so **the assumption survives** — the undefined lines are the whole population of greppable bad writes, and v0.17.0 closed the path that produced them.

Consequence actually taken: [[Refuse a write whose content is empty or literally undefined]] shipped in v0.18.0 as a TRIPWIRE for one known shape rather than as the primary fix. That is precisely the decision this test existed to make, and it was made from the number rather than from the preference of the party that wanted to build the guard.

CAVEAT THE TEST ALREADY NAMED, restated because it still holds: nothing here can see a write that was well-formed and WRONG. A correct-looking annotation on the wrong node is invisible to every check run here, and remains the genuinely alarming shape.

TWO BUGS IN THE SWEEP had to be fixed before its number meant anything, and both were the failure mode this tree keeps meeting — a check that quietly measures nothing. (1) Git quotes non-ASCII paths in --name-only, so git show failed on the vault's em-dashed filenames and the sweep SKIPPED FOUR AFFECTED FILES WITHOUT SAYING SO. (2) Merge commits re-counted entries already counted on the side branch. The first run reported a clean, confident, wrong number: 5 and 12 where the truth was 6 and 15. Filed as [[A sweep that cannot read its subject reports a clean result]].

Also corrects the v0.17.0 changelog, which recorded fourteen lines split 8 meta / 6 tetrix — wrong in both the total and the split. Corrected in the v0.18.0 entry, not edited in the old one.
