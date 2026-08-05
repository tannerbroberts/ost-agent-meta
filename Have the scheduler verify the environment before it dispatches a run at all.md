---
type: Solution
source: 'agent:ideation-2026-08-03'
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The scheduler's view of the environment matches what the run itself would see]]

Make readiness the scheduler's problem, not the pass's. Before firing a scheduled run, the thing that fires it confirms the vault is reachable and the required tools resolve; if not, it does not dispatch, and it reports the skip against the schedule rather than against the run.

**The trade it makes:** it is the only sibling that avoids spending the compute at all, and it puts the failure where the fix lives — a toolless environment is a configuration fact about the host, not an event inside a pass. It also gives the missing accumulating signal almost for free: a scheduler that skips has a natural place to count consecutive skips and escalate, because it persists across runs in a way a pass does not.

**The price is that it needs a scheduler that can do this**, and the surface may not offer one. It also duplicates knowledge — the scheduler must know what the pass requires, so the requirement now lives in two places and can drift. Deriving the check from the same declaration "Declare the tool surface a pass requires and abort in the first second if it is absent" uses would fix that, which suggests these two are complements rather than true alternatives; a human should rule on whether to build both.

**How it differs from its siblings.** Sibling one aborts after starting; this prevents starting. "Fall back to the command-line path automatically when the MCP tools are absent" starts and finishes anyway, at reduced capability.

Distinguishing assumption: that the scheduler's view of the environment matches the run's. If the scheduler checks from a different shell, user, or working directory than the run gets, a green preflight proves nothing — and the evidence under "A recorded failure can't be reproduced, because the record omits where it ran" is a case of exactly that divergence.

## Definition of done

"Compare the scheduler's view of the environment against the run's"

```
npx vitest run test/loop/preflight-parity.test.ts
```

Green means ten consecutive dispatches agreed *exactly* between what the scheduler saw at dispatch time and what the run itself read in its first second — working directory, resolved `PATH`, user, and vault reachability, not just tool presence. One disagreement fails it. It is red today because neither reading is taken anywhere.

**Why parity is the definition of done rather than "the preflight passes".** The claim this solution makes is that the preflight is *authoritative*. A preflight that checks from a different shell, user, or working directory than the run will get is not a safety check, it is a hint — and a hint wired to prevent dispatch will eventually cancel a run that would have worked, which is a worse failure than the one it was added to prevent. This vault has already paid for exactly that divergence once; the evidence is on "A recorded failure can't be reproduced, because the record omits where it ran", where a step failed purely because it ran from a directory nobody recorded.

**What green does NOT settle.** Parity across ten dispatches on one machine says nothing about a scheduler and a run that live on different hosts, in different containers, or under a different user — the case where divergence is likeliest and this command is least informative. It also says nothing about whether aborting early is what an operator wants; a run cancelled on a preflight that was right is still a run that did not happen, and whether that trade is acceptable is a person's call.

**A failure here is not a refutation of the solution.** It would say the check must run *inside* the dispatched context rather than in the scheduler's — a different design, and still a valuable one.

## History
- 2026-08-05 unlinked "Compare the scheduler's view of the environment against the run's" — moved under "The scheduler's view of the environment matches what the run itself would see" — the belief this test measures now has a node of its own
