---
type: Assumption
source: 'agent-run:unattended-sweep-2026-08-29'
created: '2026-08-29'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion
[[The split reports defaulted-parked apart from labelled-parked, rather than folding both into one number]]

**Kind: feasibility, with a usability failure hiding inside it.** The candidate's appeal is that it adjudicates nothing — it just reads the `lane` field already on each test through `computeMayRun` and reports two numbers instead of one. That is only honest if the field actually distinguishes a considered verdict from an unlabelled default.

It probably does not. `src/knowledge/lanes.ts` sends anything unrecognised or missing to `CAUTIOUS_LANE`, which is `humans-required`, and this sweep's own response reports 473 tests in `needsHumans` against 0 `runnable`. Read naively, a two-column report would print "0 actionable, 65 parked" and invite exactly the misreading it was built to prevent — the operator would conclude 65 entries had been judged deliberate when most were never judged at all.

Stated so it could be wrong: a split derived from the stored lane field reports how much has been *decided*, and not merely how much has been *defaulted*.

The likely repair is a third figure — labelled-parked versus defaulted-parked — which is a change to this candidate, not an abandonment of it. That is what makes this the assumption worth testing first: it is cheap, it is answerable from the repository, and the answer changes the design rather than killing it.

**What it leaves untouched.** Whether the operator budgets differently once they see two numbers. That is a fact about a person and no spec reaches it.
