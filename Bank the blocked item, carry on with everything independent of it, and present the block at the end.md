---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Enough of a run's remaining work sits independent of whatever blocked it]]

Reaching something only the operator can do is not a reason to stop. The run records what it needs, sets that item aside, and continues with everything that does not depend on it. The operator hears about the block when the run has exhausted its independent work, alongside everything that got done in the meantime.

The word "whole" in the opportunity is what this attacks. One blocked item halting an entire loop is a scheduling failure, and the loop usually has other work available that nobody is waiting on.

**Compared to the alternatives.** The only option that reduces the cost of the wait rather than shortening it, and it works even when the operator is genuinely unavailable — asleep, on holiday, gone for the week. It needs the run to know which work depends on the blocked item, which is not always knowable, and it delays the notification, so a block the operator could have cleared in seconds now waits for the run to finish everything else.

**What would make this the wrong pick.** If most of the run is downstream of the blocked step, there is nothing to carry on with, and the operator now learns about the block later than they would have. Whether that is the common case is a question the run journals could answer.

## Test

[[Take ten past blocked runs and measure how much work sat independent of the block]]

`npx vitest run test/loop/blocked-run-independent-work.test.ts`

Green when the dependency walk over ten captured blocked runs shows a material share of outstanding work needed nothing the block was waiting on. Retrospective and model-reconstructed — a run in the moment lacks that view. It counts work, not value, and it cannot see a dependency the transcript never made explicit, which is exactly the case where carrying on does damage.

## History
- 2026-08-05 unlinked [[Take ten past blocked runs and measure how much work sat independent of the block]] — moved under [[Enough of a run's remaining work sits independent of whatever blocked it]] — the belief this test measures now has a node of its own
