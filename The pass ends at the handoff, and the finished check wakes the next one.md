---
type: Solution
status: unvalidated
created: '2026-08-02'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A pass can record enough state to be resumed without repeating work or inventing any]]

Stop treating the wait as part of the pass. When the loop reaches a point where it can only wait, it records where it got to and exits; the check's completion is what starts the next pass, which picks up from the recorded state.

**Compared with the alternatives:** this is the only candidate where waiting costs nothing at all, because nothing is running during it. It also fits the failure the tree already knows about — a run that dies mid-wait currently loses everything after the handoff. Its cost is that the loop now needs durable state between passes and something to deliver the wake, which is real infrastructure; and it converts one long session into several, so anything the agent was holding in its head has to be written down. That last consequence may be a benefit disguised as a cost.

Unvalidated, agent-ideated: a candidate for comparison, not a recommendation.

## Definition of done

[[Resume three handed-off passes from their recorded state and check they continue correctly]]

```
npx vitest run test/loop/pass-resume-fidelity.test.ts
```

Green means three passes driven to a wait, serialized, and restarted from the record alone each take the same next action the original took — no work repeated, no state invented. It is red today because a pass has no handoff record to resume from.

**The comparison is against what the original actually did next, not against whether the resumed pass looked healthy.** That distinction is the test. A resumed pass that quietly starts from a different understanding will not error; it will proceed confidently, and everything it builds on the wrong belief looks finished. Asserting only "it continued without crashing" would pass on exactly the failure worth catching.

**What green does NOT settle.** It proves the state a pass knows it is holding survives the handoff. Whatever a pass was holding implicitly — a reading of the tree it never wrote down — is absent from the record and therefore absent from the comparison, so this cannot detect a category of context that was never a candidate for serialization in the first place.

## History
- 2026-08-05 unlinked [[Resume three handed-off passes from their recorded state and check they continue correctly]] — moved under [[A pass can record enough state to be resumed without repeating work or inventing any]] — the belief this test measures now has a node of its own
