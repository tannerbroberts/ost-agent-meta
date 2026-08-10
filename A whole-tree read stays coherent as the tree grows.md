---
type: Assumption
source: 'agent-ideation:2026-08-09-unattended-sweep'
created: '2026-08-10'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Run re-synthesis against a vault larger than every cap and require it to see every node]]

**The belief, stated so it can be false.** Re-synthesis works by reading the entire tree at once and proposing how it should be reorganised. That only means anything if the read is actually entire. This assumption is that a whole-tree read stays coherent — complete, and understood to be complete — as the tree grows.

This is the feasibility risk the solution names in its own body: "that a whole-tree read stays coherent as the tree grows (feasibility)". It was never given a node, so the only test beneath the solution was the desirability one about whether a human accepts the proposals. That left the cheaper and more likely failure untested.

**Why it is probably false already, from first-party observation this pass.** This vault holds 1158 nodes, and every whole-tree channel available to an agent is capped:

- `ost_read_tree` truncates on a tree this size and says so — its own description states "On a large tree the listing is capped to keep the response readable", returning `shown`/`hidden` counts rather than the tree.
- `ost_next_work` caps every list at 25. This pass saw 25 of 88 unmapped evidence items, 25 of 62 solutions missing instruments, and 25 of 347 assumption tests.

So the input a re-synthesis pass would actually receive today is a sample, not the tree. The danger is not that the read fails — it succeeds, and reports a number. The danger is that a reorganisation proposal computed over the visible fraction is presented as a whole-tree re-synthesis, and merges, splits and retirements are proposed against nodes whose duplicates were never in the window.

**This is not hypothetical on this tree.** The census recorded on "A pass that cannot see the repository cannot set an instrument at all" classified 25 of 62 queue entries and had to state plainly that "the remaining 37 of 62 were not listed by the tool and were not classified", and that a capped list is alphabetical rather than random — not a reason to think it unrepresentative, and not a reason to think it representative either. That is exactly the failure this assumption predicts, already happening to a smaller analysis than re-synthesis.

**Why it could still be true.** A re-synthesis implementation need not go through the agent-facing tools at all; it could read the vault directory itself, where nothing is capped. If it does, this assumption holds and the risk is only that a *reader* of the proposal assumes the agent's own view was uncapped. The test below is written to tell those two cases apart.

**Grounded against the repository, 2026-08-09.** `src/ost/` holds `sweep.ts` and `census.ts` but no re-synthesis module, and `test/ost/` holds no re-synthesis spec. It does hold `dedupe-scale.test.ts`, so scale specs are an established pattern in this suite rather than a new kind of thing to ask for.

⚠️ Unvalidated. Agent-ideated.
