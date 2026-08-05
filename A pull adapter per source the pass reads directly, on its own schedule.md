---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[An adapter against a passive source can be built quickly and keeps working without attention]]

For each system holding experiment data, a small read-only adapter that knows how to query it and how to render what it finds as an evidence record. The pass runs the adapters itself at the start of every sweep, the same way it already reads its drop folders. The human's job shrinks to enabling an adapter once and saying where to point it.

The vault already has the shape of this — the ingest surface reports per-channel results and can say a channel is disabled or unreadable and why. Experiment sources would be more of the same rather than a new concept.

**Compared to the alternatives.** Adapters put the schedule under the reader's control, which matters when the source has no notion of pushing and no watched folder to write to. That independence is also the cost: every source needs its own adapter written and maintained, and a source that changes its API breaks a channel silently unless the per-channel error reporting is honest about it.

**What would make this the wrong pick.** If the sources in question already emit webhooks or already write scheduled exports, an adapter is a worse version of a thing that exists. Adapters earn their keep exactly where the source is passive.

## Test

"Write one adapter against the messiest source and time how long it stays working"

`npx vitest run test/adapters/messiest-source-replay.test.ts`

Green when the adapter parses every historical snapshot of that source in order. Durability by proxy — it means "would not have broken over the period on record", never "will not break next". It is blind to auth, rate-limit and endpoint changes, which are the failures that actually kill pull adapters.

## History
- 2026-08-05 unlinked "Write one adapter against the messiest source and time how long it stays working" — moved under "An adapter against a passive source can be built quickly and keeps working without attention" — the belief this test measures now has a node of its own
