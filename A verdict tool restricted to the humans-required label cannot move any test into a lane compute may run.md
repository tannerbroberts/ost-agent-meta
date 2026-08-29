---
type: Assumption
source: 'agent-run:unattended-sweep-2026-08-29'
created: '2026-08-29'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

**Kind: feasibility.** The whole safety argument for putting this verdict on the unattended surface is directional — the tool can only ever shrink what compute may run, so an agent using it costs itself work rather than clearing its own gate. That argument is a claim about code, and it could be false in a way nobody would notice: if the write path can reach any lane whose `computeMayRun` is true, or if an unrecognised label is ever read as runnable, the one-way property is gone and the grant becomes the self-permit it was designed not to be.

Stated so it could be wrong: *every* label this tool can write resolves to `computeMayRun === false`, and there is no argument, no default and no fallthrough that reaches `compute-only`.

`src/knowledge/lanes.ts` makes this plausible rather than certain — `computeMayRun` already fails closed on an unknown or missing lane, and `CAUTIOUS_LANE` is `humans-required`. Plausible is not the same as pinned, and nothing in the suite currently pins it for this write path, because this write path does not exist yet.

**What settling this does not settle.** Nothing about whether the operator wants the grant at all. That belief is desirability and sits on the sibling assumption; a green here would say only that the mechanism is as narrow as claimed.
