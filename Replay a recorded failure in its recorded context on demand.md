---
type: Solution
source: 'agent:ideation-2026-08-03'
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Enough recorded steps are side-effect-free to be safely replayable by a fixed rule]]

Rather than trying to record enough context to explain a failure, make the record executable: a recorded step can be re-run, in the directory and with the arguments it originally used, and the outcome of that re-run is appended beside the original. The operator asks "does this still fail?" and gets an answer instead of a reconstruction.

**The trade it makes:** it collapses the whole class of "looks complete, cannot be believed" records that this opportunity is about — a replay that passes tells you the failure was environmental, a replay that fails hands you a live reproduction to debug. The price is real: replay executes something, so it is only safe for steps that are side-effect-free, and deciding which those are is a judgement the tool does not have. It also cannot replay a context that no longer exists.

**How it differs from its siblings.** "Snapshot the resolved environment, but only for the step that failed" makes the record self-describing and readable anywhere; this makes it re-runnable but only on a machine that still resembles the original. That is the core trade-off between the two — portability of explanation versus certainty of answer.

**The strongest version of this may be the narrow one:** replay only steps the loop itself issued and already knows to be read-only, which is most of the check-shaped ones (`vitest`, `tsc`, `ost-agent check`) and none of the publishing ones.

Distinguishing assumption: that operators would trust a replay result enough to close a failure on it, rather than re-running by hand anyway — which is the very habit this opportunity says is eating the value of recording.

## Definition of done

"Count how many recorded steps are safely replayable at all"

```
npx vitest run test/loop/replayable-step-share.test.ts
```

Green means at least 60% of recorded steps from the last thirty days classify as side-effect-free under a **fixed rule written before the distribution was looked at** — a committed allowlist of read-only verbs — with steps needing a human decision counted as failures of the rule rather than passes. It is red today because no allowlist is committed and nothing classifies steps for replayability.

**The ordering is the load-bearing part of this command, not the threshold.** Deriving the allowlist from the sample and then scoring the sample against it would produce a number that means nothing and looks identical to one that does. Any implementation of this spec has to commit the rule as data before it reads the corpus, or the green is worthless.

**Why 60% and what each side implies.** Below it, replay covers a minority of failures and "Snapshot the resolved environment, but only for the step that failed" is the better bet for this row. Above it, the narrow version named in this node's body — replay only steps the loop itself issued and already knows to be read-only — is worth building. So a red result here does not kill the row; it redirects it to the sibling.

**What green does NOT settle.** Whether an operator would actually close a failure on a replay result rather than re-running it by hand anyway. That habit is the entire value this solution claims to recover, and it needs a person to answer — no share of replayable steps implies anyone will trust the replay.

## History
- 2026-08-05 unlinked "Count how many recorded steps are safely replayable at all" — moved under "Enough recorded steps are side-effect-free to be safely replayable by a fixed rule" — the belief this test measures now has a node of its own
