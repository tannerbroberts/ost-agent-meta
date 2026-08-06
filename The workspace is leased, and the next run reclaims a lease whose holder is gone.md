---
type: Solution
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A dead lease holder can be told from a slow one without waiting out the TTL]]

**The idea.** Treat the shared workspace the way this product already treats the loop itself: a run takes a lease on it, stamped with its id and a heartbeat, and releases it on exit. A run that finds a held lease checks whether the holder is still alive; an expired lease is reclaimed and the workspace reset, a live one means back off rather than break in.

**Approach:** *lifecycle*. Keep the shared resource and make ownership explicit and expiring.

**Why this shape and not a new invention.** The vault config already runs this exact pattern for the firing loop — `loop.lockTtlMinutes: 60`, with the comment that "a firing still holding the lock after this is assumed dead." That is a lease with a TTL, already chosen, already tuned, already understood by whoever operates this. Applying it one level down to the workspace reuses a mechanism the operator has a mental model of, instead of adding a second, differently-shaped answer to "who owns this right now."

**Contrast with its siblings.** It is the only one that keeps the warm workspace *and* is safe under overlap — reconciliation gets the first and not the second, per-run naming gets the second and not the first. That is also why it is the most machinery: it needs a liveness signal, a TTL, and a reset path, where reconciliation needs a stat and per-run naming needs a string.

**Where it fails.** TTL-based liveness is a guess wearing a number. Set it short and a slow-but-healthy run gets its workspace stolen mid-build, which is the destructive failure reconciliation has, reintroduced through the front door. Set it long and a dead run blocks the loop for up to that long — the failure this whole opportunity is about, merely bounded instead of removed. The `lockTtlMinutes: 60` precedent shows the product already accepts an hour of that exposure for the loop, but a workspace is held for minutes rather than an hour, so the loop's number is precedent for the shape and not for the value.

**Cost.** The largest of the three. A lease file, heartbeat writes, an expiry check, and a reset path — plus a decision about what a reclaiming run does with whatever the dead one left in the tree.

⚠️ Unvalidated. Agent-ideated from one observed failure.
