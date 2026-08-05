---
type: Solution
source: 'agent:ideation-2026-08-03'
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The text at the intended site contains what a correct retry needs]]

Do not try to detect drift. Make one failure enough. When an edit does not match, the refusal returns the text that *is* at the intended site — the nearest near-miss, with enough surrounding context to re-anchor — so the agent can correct on the next call instead of re-reading the file and starting over.

**The trade it makes:** the cheapest of the three by a wide margin, purely a change to a message, no new state and no watcher. It is also the only one that helps when the mismatch was *not* drift — a misremembered string, whitespace, an escape sequence — which the evidence suggests is a real share of these failures. The price is that it never prevents anything; it makes recovery cheap and leaves the wasted call spent.

**Why it may be the highest-value one anyway.** The vault's own diagnosis of this class of problem, in [[Two thirds of my calls failed, and each one only told me after I made it]], is that refusals should *name the near-misses so one failure resolves the question*. That node reached the same conclusion from a different channel — 62 failed calls in a day, spent on reconnaissance through the error channel. Two independent lines of evidence converging on the same fix is worth a human's attention when choosing among these three.

**How it differs from its siblings.** [[Carry a content hash from read to write and refuse on drift, naming what drifted]] tells you *why* the edit failed. This tells you *what to do next*. Those are complements, and shipping both costs barely more than either — the hash supplies the cause, the near-miss supplies the correction.

**Adjacent variant:** address edits by anchor or structure rather than literal string match, so formatting churn stops breaking the address at all. Distinct enough to be its own candidate if a human wants a fourth.

Distinguishing assumption: that the intended site is identifiable when the exact string is not. If the old text is gone entirely, there is no near-miss to show and this returns nothing useful.

## Definition of done

[[Check whether the near-miss text would have supplied the correction]]

```
npx vitest run test/mcp/refusal-shows-current-text.test.ts
```

Green means the recorded failed edits each come back with the text actually present, and that text contains what the caller needed to correct itself — the difference between a refusal and a diagnosis. It does not settle whether a caller handed the correction actually uses it rather than re-reading the whole file anyway, which only the next sessions' traces show.

## History
- 2026-08-05 unlinked [[Check whether the near-miss text would have supplied the correction]] — moved under [[The text at the intended site contains what a correct retry needs]] — the belief this test measures now has a node of its own
