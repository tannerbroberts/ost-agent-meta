---
type: Assumption
source: 'agent-ideated:2026-08-22-unattended-sweep'
created: '2026-08-22'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Delete each guard behind a claimed refusal in turn and require the suite to redden every time]]

**The belief, stated so it can be false.** This solution sells four specific refusals — the tool "cannot mark its own output validated, cannot invent the outcome, cannot record a test result it did not watch a human run, and caps every claim at the rung its source actually earned." The position is only as good as the weakest of the four, and it depends on a property nobody has written down: that each named refusal is bound to a guard, such that removing the guard turns something red before the sentence is read by a prospect.

**Why it is the mechanical half.** The sibling assumption, "Buyers treat refusals as trustworthiness rather than as the product being worse", is a buyer's belief and is correctly a person's to measure. This one is not about buyers. It asks whether the sentences are true and stay true, and a spec answers it.

**Grounds, first-party, and the precedent that makes this concrete.** This is not a hypothetical failure mode — this repository has already had it, in the same shape and in four places at once. Until 2026-07-29, `README.md`, the Claude Code consumption guide, the unattended-pass example and the *generated* `SKILL.md` each promised some version of "the worst thing it can do is make a commit that doesn't make sense", which was false: `ost_append_to_node` could write the `## Results` heading a gate reads, and `ost_set_status("validated")` passed the invariants. The repair was `test/release/withdrawn-claims.test.ts`, which scans the operator-facing surfaces and fails if any wording of that claim returns.

That guard is the *negative* half — a retired claim may not come back. There is no positive half. Nothing binds a refusal the copy currently asserts to the guard that makes it true, so the next claim to drift does so exactly the way the last one did, and is caught the same way: by someone noticing, months later. The `docs/reference/v1-readiness.md` criteria (B1, B2, B10, P10) name the guarantees; the copy names them again in its own words; the two are joined only by whoever wrote both.

**What turns on it.** If false, the strongest available position is being built on sentences whose truth nobody re-checks — which is the one failure a position about trustworthiness cannot survive being caught in. If true, the position is the rare marketing claim a sceptic can verify by running the suite, and that is the actual product being sold.

⚠️ Unvalidated. Agent-ideated from first-party reads of `test/release/withdrawn-claims.test.ts` and `src/ost/results.ts`.
