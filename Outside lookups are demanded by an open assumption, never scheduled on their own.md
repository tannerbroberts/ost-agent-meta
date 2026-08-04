---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Count how many open assumptions in this tree could be moved by anything public at all]]

Nothing searches on a timer. Instead, every open assumption that could be moved by public information carries the question it would need answered, and lookups are spent only against that list, cheapest question first. A finding enters the tree already attached to the thing it bears on.

The failure this avoids is the one that makes autonomous research expensive and useless at the same time: findings that are individually interesting and attached to nothing, which then have to be read by a human to discover they changed no decision.

**Compared to the alternatives.** Against a scheduled research loop, this trades coverage for relevance — it will miss things nobody thought to ask about, and it will never surface the surprise that reframes the whole branch. Against a subscription, it is far more targeted but much slower to notice a change in a source that matters. Its real advantage is that the spend is justified per lookup before it happens, which the other two cannot claim.

**What would make this the wrong pick.** It can only ask questions the tree already knows to ask. A vault whose blind spots are its problem will get very efficient answers to the wrong questions, and the efficiency will make that harder to notice.

## Definition of done

[[Count how many open assumptions in this tree could be moved by anything public at all]]

```
npx vitest run test/web/public-movable-assumptions.test.ts
```

Green means each open assumption is labelled by whether public material could move it — the count that says whether demand-driven lookups would have anything to do. Worth expecting a low number and treating that as the finding: most of this tree's open assumptions are about its own operator and its own code, neither of which anything public knows about. It does not settle whether a lookup that *is* demanded would find anything.
