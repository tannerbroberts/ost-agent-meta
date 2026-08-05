---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A sweep maintained from returned deltas stays exactly in step with a fresh read]]

A mutating call already knows what it changed about the outstanding picture. Creating a solution under an under-served opportunity moves that opportunity's count and adds a solution with no assumption test. Return that as part of the write's own result, and a caller can maintain an accurate sweep locally without asking for one.

The re-reads exist because writes currently answer only "done" when they could answer "done, and here is what that changed."

**Compared to the alternatives.** Removes the calls entirely rather than making them cheap, which is the only version of this that shows up in a trace. The caller's picture also stays current continuously instead of in jumps. The cost is that every write must compute its consequences correctly, and a write that computes them wrongly leaves the caller confidently out of step with the tree — a failure with no symptom until something surprising happens.

**What would make this the wrong pick.** It is only correct while the caller is the sole writer. In a vault two agents share, a locally maintained sweep drifts silently, and the re-read this replaces was the thing that would have caught it.

## Definition of done

[[Maintain a sweep from returned deltas alone across a full pass and compare against a fresh read]]

```
npx vitest run test/mcp/sweep-delta-consistency.test.ts
```

Green means a sweep accumulated from returned deltas alone, over more than a hundred writes and never once reconciled against the tree, matches a fresh read field for field. It is red today because writes return no delta at all.

**Exact agreement is the bar, and "close" is the failure mode this is guarding against.** A write that computes its consequences wrongly leaves the caller confidently out of step with the tree, and that state has no symptom — nothing looks wrong until a much later call acts on a count that was quietly stale a hundred writes ago. A near-match is that failure, already present, merely small so far.

**Why the sample size is in the threshold.** Divergence compounds; ten writes can agree by luck. This vault's own passes routinely exceed two hundred writes, so a hundred is a realistic single-run sample rather than a stress figure.

**What green does NOT settle.** It assumes a single writer, which is exactly the condition under which delta accumulation is correct by construction. The interesting failure is drift when a second agent is writing to the same vault, and this command is blind to it — that needs a concurrent arm, and [[Two agents sharing my vault can trample each other]] is where the cost of getting it wrong is already recorded.

## History
- 2026-08-05 unlinked [[Maintain a sweep from returned deltas alone across a full pass and compare against a fresh read]] — moved under [[A sweep maintained from returned deltas stays exactly in step with a fresh read]] — the belief this test measures now has a node of its own
