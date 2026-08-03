---
type: Solution
source: 'agent:ideation-2026-08-03'
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

Make readiness the scheduler's problem, not the pass's. Before firing a scheduled run, the thing that fires it confirms the vault is reachable and the required tools resolve; if not, it does not dispatch, and it reports the skip against the schedule rather than against the run.

**The trade it makes:** it is the only sibling that avoids spending the compute at all, and it puts the failure where the fix lives — a toolless environment is a configuration fact about the host, not an event inside a pass. It also gives the missing accumulating signal almost for free: a scheduler that skips has a natural place to count consecutive skips and escalate, because it persists across runs in a way a pass does not.

**The price is that it needs a scheduler that can do this**, and the surface may not offer one. It also duplicates knowledge — the scheduler must know what the pass requires, so the requirement now lives in two places and can drift. Deriving the check from the same declaration [[Declare the tool surface a pass requires and abort in the first second if it is absent]] uses would fix that, which suggests these two are complements rather than true alternatives; a human should rule on whether to build both.

**How it differs from its siblings.** Sibling one aborts after starting; this prevents starting. [[Fall back to the command-line path automatically when the MCP tools are absent]] starts and finishes anyway, at reduced capability.

Distinguishing assumption: that the scheduler's view of the environment matches the run's. If the scheduler checks from a different shell, user, or working directory than the run gets, a green preflight proves nothing — and the evidence under [[A recorded failure can't be reproduced, because the record omits where it ran]] is a case of exactly that divergence.
