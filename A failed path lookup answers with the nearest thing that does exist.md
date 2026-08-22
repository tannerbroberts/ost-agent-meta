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

## Observed running in production, on one surface — unattended sweep, 2026-08-22

This candidate is described here as an idea. It is **already built inside `ost_read_repo`**, and a session captured this pass shows it working, twice, on the exact failure shape this node was written from.

`TRANSCRIPT:8f938a9e-6551-4b75-bd8b-5e605da81ff8` (this vault's own unattended firing, nobody watching) recorded two `ost_read_repo` tool errors:

- `"src/ost/rollup.ts" does not exist in OST-Agent — OST-Agent/src/ost exists and contains briefing.ts, census.ts, dedupe.ts, extent.ts, frontmatter.ts, headings.ts, instrument.ts, lanes.ts, migrate.ts, node.ts, pending-ask…`
- `"src/processes/map.ts" does not exist in OST-Agent — OST-Agent/src/processes exists and contains tree.ts, types.ts; nothing there is close enough to name, so this is not a typo to correct`

Both are precisely the response this node specifies: how far down the path was valid, what is actually present at that point, and a near match where one exists.

**The second one answers this node's own stated risk.** The prose above warns that "suggesting near-matches invites taking them" — that a caller told *did you mean* will sometimes say yes when the real answer is that something is wrong further upstream. The shipped implementation declines to suggest when nothing is close, and says so in words: *"nothing there is close enough to name, so this is not a typo to correct."* The named failure mode was designed against rather than accepted.

**The scope is one surface, and the gap is the rest.** This is live for `ost_read_repo` only. The failures this node was originally distilled from — `sed: src/cli/index.ts`, `cd: docs/reference`, `ls: /Users/tanner/dev/ost-agent-meta` — came through the harness's own shell and file tools, which this product does not own and cannot make answer this way. So the mechanism is proven computable and adopted where we control the call, and unavailable where most of the recorded misses actually happened. The definition of done above (`test/cli/path-near-miss.test.ts`) still names a spec that does not exist, so nothing here is a recorded result.

**For a human to decide, not this pass:** whether `status` should move to `shipped` for the `ost_read_repo` surface while the CLI path stays open, or whether the node should be split so the built half can close and the unowned-surface half can be judged on its own. Left `unvalidated` here because "shipped" over a node whose stated done-condition covers two surfaces would overstate what was observed.

_Source: `TRANSCRIPT:8f938a9e-6551-4b75-bd8b-5e605da81ff8`, read in full this pass. Observed behavior of this product's own tool, captured mechanically. Grounds feasibility and usability, not demand — nobody chose this, an agent hit it. No command executed, no result recorded, rung unchanged at the `assertion` floor._
