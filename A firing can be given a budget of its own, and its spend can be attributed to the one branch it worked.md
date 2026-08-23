---
type: Assumption
source: 'REPO:OST-Agent/src/config/schema.ts'
created: '2026-08-23'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

**The belief, stated so it could be false:** the mechanism above says a deep-dive firing "spends its whole budget thinking about one branch." Both halves of that sentence are mechanical claims — that a firing can be *given* a budget of its own, and that afterwards anyone can tell from stored records *which branch* it spent on. If either is false, a deep-dive is indistinguishable from a sweep once it is over, and the operator cannot audit the thing they are being asked to pay an hour of compute for.

**Both halves are false today, read first-party from source this pass.**

- **No per-firing budget exists.** `LoopSpendSchema` (`src/config/schema.ts`) declares exactly three fields: `ceilingWeightedTokens`, `windowHours`, `sessionsDir`. That is one rolling window across the whole vault, stamped at `loop start` and enforced between firings and at phase boundaries — `test/loop/spend-ceiling.test.ts` specs precisely that behaviour, including that widening the config mid-firing widens nothing. A firing cannot be allotted a budget; it draws on a shared window until the ceiling refuses it. So "its whole budget" names nothing the product has.
- **No branch attribution exists.** `UsageEvent` (`src/telemetry/usage.ts`) carries `ts, tool, ok, ms, surface, argBytes, err, denied, session, unknown, wrote` — and nothing else. `surface` reads `mcp` for a sweep and for a deep-dive alike. `unknown` attributes a call to an `#Unknown` node, which is a different axis. `wrote` names files a call *created*, and a deep-dive that appends analysis to existing nodes creates none, so it is empty for exactly the firing type this solution proposes.

**The honest qualification, so this is not over-read.** Branch attribution is partially recoverable *outside* the trace: every mutating MCP call commits with the node's title and `source:` in the message (`provenanceSuffix` in `src/mcp/server.ts`), so a person could reconstruct a firing's branch from `git log`. That is a reconstruction by hand, not a stored attribution, and it is the operator's hours — the resource this whole tree treats as the scarce one.

**What this is not.** It says nothing about whether analysis-only firings change decisions, which is the sibling assumption beneath this solution and is correctly a person's. This is the feasibility half: whether the mechanism as described can be built and audited at all.

_Method: first-party `ost_read_repo` of `src/config/schema.ts`, `src/telemetry/usage.ts` and `test/loop/spend-ceiling.test.ts`, all read in full (`truncated: false`), plus a listing of `test/loop/`. Nothing executed. Rung stays at the `assertion` floor._
