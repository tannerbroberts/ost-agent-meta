---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-25-friction-a-pass-that-dies-on-a-driver-error-still-exits-0.md'
created: '2026-07-25'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**The idea.** Adopt-existing lane: the tree already carries 'Supervisor heartbeat with automatic restart' under the unattended branch. Extend its contract: heartbeat reads `.ost-agent/runs/*.json`, treats `error` fields as failures, restarts or alerts. No new failure channel — the journal becomes the protocol.

**Contrast with siblings:** the only lane that acts (restart/alert) rather than reports; heaviest, depends on the supervisor existing at all.

**Trade-off:** couples two unbuilt things together; its test must not presuppose the supervisor.
