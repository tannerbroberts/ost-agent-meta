---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

When a path does not exist, do not stop at saying so. Report how far down the path was valid, what is actually present at that point, and the closest match if there is an obvious one. `/Users/tanner/dev/ost-agent-meta: no such directory — /Users/tanner/dev exists and contains OST-Agent, ost-benchmarks; did you mean /Users/tanner/ost-agent-meta?`

One failed lookup then costs one call instead of three, because it answers the question the caller was actually asking rather than the one they literally typed.

**Compared to the alternatives.** Needs nothing up front, carries no staleness, and scales to any path anywhere rather than to whatever a map happened to cover. It still spends a call per miss, which a workspace map would have avoided entirely, and it helps only once the caller is already close.

**What would make this the wrong pick.** Suggesting near-matches invites taking them. A caller told "did you mean this other directory" will sometimes say yes when the answer is that the directory it wanted does not exist and something is wrong further upstream — and a helpful suggestion is how that goes unnoticed.
