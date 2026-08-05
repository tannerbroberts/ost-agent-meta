---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The nearest existing path is usually the one the caller meant]]

When a path does not exist, do not stop at saying so. Report how far down the path was valid, what is actually present at that point, and the closest match if there is an obvious one. `/Users/tanner/dev/ost-agent-meta: no such directory — /Users/tanner/dev exists and contains OST-Agent, ost-benchmarks; did you mean /Users/tanner/ost-agent-meta?`

One failed lookup then costs one call instead of three, because it answers the question the caller was actually asking rather than the one they literally typed.

**Compared to the alternatives.** Needs nothing up front, carries no staleness, and scales to any path anywhere rather than to whatever a map happened to cover. It still spends a call per miss, which a workspace map would have avoided entirely, and it helps only once the caller is already close.

**What would make this the wrong pick.** Suggesting near-matches invites taking them. A caller told "did you mean this other directory" will sometimes say yes when the answer is that the directory it wanted does not exist and something is wrong further upstream — and a helpful suggestion is how that goes unnoticed.

## Definition of done

"Generate near-miss suggestions for past failures and count how many point at the right thing"

```
npx vitest run test/cli/path-near-miss.test.ts
```

Green means the recorded failed lookups — `src/cli/index.ts`, `docs/reference`, `report2.txt`, and the missing node file — each come back with the path that was actually meant. It settles that the suggestion can be computed; it does not settle whether being handed a near miss stops the caller guessing again, which only the next few sessions' traces can show.

## History
- 2026-08-05 unlinked "Generate near-miss suggestions for past failures and count how many point at the right thing" — moved under "The nearest existing path is usually the one the caller meant" — the belief this test measures now has a node of its own
