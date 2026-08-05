---
type: Solution
source: 'agent:ideation-2026-08-03'
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A hash guard refuses almost no good writes while correctly naming the ones that were drift]]

Every read hands back a fingerprint of the file as it was. Every write presents that fingerprint. If the file has changed since, the write is refused with a message that says *the file changed since you read it* — not *your string was not found* — and names what moved.

**The trade it makes:** it converts a confusing failure into an accurate one at near-zero cost, and it is the only sibling that distinguishes the two causes the current refusal conflates. Today `String to replace not found in file` means either "you misremembered" or "someone else edited it", and those need opposite responses. The price is that it detects drift only at write time, so the wasted composition is still wasted — it fixes the diagnosis, not the loss.

**How it differs from its siblings.** "Watch the working tree and invalidate the agent's copy the moment an external write lands" catches the change *before* the agent builds on it, which is strictly earlier but needs a watcher. "Make the refusal show the text that is actually there now" does not detect drift at all — it makes recovery from any mismatch cheap. This one sits between them: cheap like the third, accurate like the second.

**Why the accuracy matters more than it looks.** Session `5960b7ec` recorded the tool exhausting its own guesses — *"Edit also tried swapping \uXXXX escapes and their characters; neither form matched, so the mismatch is likely elsewhere in old_string"* — and concluding the agent's string was wrong. If the file had drifted, that diagnosis sent the agent hunting in the wrong place.

Distinguishing assumption: that reads and writes are close enough together in the loop for a fingerprint to survive between them. If the agent reads a file, does twenty minutes of other work, and then writes, the hash will be stale far more often than the content is genuinely contested, and constant false refusals would make it worse than nothing.

## Definition of done

"Replay captured sessions to count how often a hash guard would refuse a good write"

```
npx vitest run test/git/read-write-hash-drift.test.ts
```

Green means the guard refuses exactly the writes whose file moved under the read — the recorded `String to replace not found in file` failures, and the session where a concurrent writer had moved HEAD and touched fourteen files — and names what drifted rather than reporting a generic miss. The count in the test's own title is the thing to watch: a guard that also refuses good writes trades one interruption for another, and this command is what makes that rate visible instead of assumed.

It does not settle what the caller should *do* on refusal, which is where the cost of being right actually lands.

## History
- 2026-08-05 unlinked "Replay captured sessions to count how often a hash guard would refuse a good write" — moved under "A hash guard refuses almost no good writes while correctly naming the ones that were drift" — the belief this test measures now has a node of its own
