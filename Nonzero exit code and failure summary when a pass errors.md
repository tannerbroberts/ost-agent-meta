---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-25-friction-a-pass-that-dies-on-a-driver-error-still-exits-0.md'
created: '2026-07-25'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Break one pass on purpose and check cron notices within a cycle]]

**The idea.** The smallest honest contract: a pass whose driver or any tool invocation errors exits nonzero and prints the error as the last line. Cron, launchd, CI — everything already speaks this protocol.

**Contrast with siblings:** the machine-legible floor; the status-surface sibling is for humans, the supervisor sibling for recovery. This one costs an afternoon and unblocks both.

**Trade-off:** partial passes (some work done, then an error) need a decision — fail the whole pass or exit a distinct 'partial' code.
