---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Send one notification per block for two weeks and count how many the operator acts on]]

When a run reaches something only the operator can do, it says so immediately — a push notification, a message, whatever they actually read — naming the exact command that would unblock it and what is queued behind it. The wait becomes an event that arrives, rather than a state discovered whenever someone next looks.

Nearly all the cost here is latency, not the blocking itself. A wait the operator learns about in ninety seconds costs ninety seconds; the same wait discovered the following morning costs a night.

**Compared to the alternatives.** The most direct answer to the opportunity as written, since the complaint is precisely that nobody is told. It is straightforward to build and it degrades safely — an unread notification leaves things no worse than today. What it does not do is reduce the number of waits, and an operator notified about every one will start ignoring them, at which point the mechanism is worse than nothing because it looks like it is working.

**What would make this the wrong pick.** It puts the operator on call. A person who receives a message every time an unattended run needs them has not been freed by automation, and may reasonably prefer to be told once a day.

## Definition of done

[[Send one notification per block for two weeks and count how many the operator acts on]]

`npx vitest run test/loop/block-notification.test.ts`

The spec asserts the notification fires at the moment the run blocks — not at the end of the pass — and carries both payloads the node says make it worth reading: the exact command that would unblock it, and what is queued behind it. Red today because a run that reaches an operator-only step records the block and tells nobody.

**What a green here does not settle, and the node is unusually clear that it is the whole question.** Latency is what this buys, and a spec can prove the message leaves immediately. Whether anyone reads it is the other half, and the node names the specific way it fails: an operator notified about every wait starts ignoring them, at which point the mechanism is *worse than nothing because it looks like it is working*. A passing suite is exactly the artifact that would make it look like it is working. The two-week count is the humans-required test and nothing here substitutes for it.
