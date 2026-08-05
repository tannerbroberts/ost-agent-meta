---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-25-friction-a-pass-that-dies-on-a-driver-error-still-exits-0.md'
created: '2026-07-25'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The run journals already contain what an alerting rule needs]]

**The idea.** Adopt-existing lane: the tree already carries 'Supervisor heartbeat with automatic restart' under the unattended branch. Extend its contract: heartbeat reads `.ost-agent/runs/*.json`, treats `error` fields as failures, restarts or alerts. No new failure channel — the journal becomes the protocol.

**Contrast with siblings:** the only lane that acts (restart/alert) rather than reports; heaviest, depends on the supervisor existing at all.

**Trade-off:** couples two unbuilt things together; its test must not presuppose the supervisor.

## Now buildable on shipped surface — 2026-07-25

v0.5.0 shipped `src/runner/journal.ts`: `readRunJournals` (newest-first, corrupt files skipped), `failed`, `lastFailedRun`, `lastRunPerProcess`. That is most of this candidate's read layer, already written and tested, and the alert rule it uses is the one the 14-journal replay supports.

**What is genuinely left, and it is the part that matters.** This candidate's value is detecting the *absence* of runs — a schedule that stopped firing — and nothing shipped touches that. It needs an expected-cadence notion (from `processes.*.cron` in the config, which already exists) and a check that compares last-run timestamps against it. That is the difference between "tells you a run failed" (done) and "tells you runs stopped happening" (not started), and only the second one makes silence trustworthy.

## History
- 2026-08-05 unlinked [[Replay the three recorded failed runs through the journal-alert rule on paper]] — moved under [[The run journals already contain what an alerting rule needs]] — the belief this test measures now has a node of its own
