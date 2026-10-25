---
type: Assumption
source: 'REPO:src/adapters/transcript.ts'
created: '2026-10-25'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion
[[extractFriction labels a same-id repeat apart from a new call and the record splits the retry count]]

**Risk category: feasibility.**

**The belief, stated so it could be false:** a session transcript carries enough to tell, for every repeated call, whether its `tool_use` id had already appeared earlier in the session. If it does, `extractFriction` can label each retry with that fact and `renderBody` can split the count.

**Why this belief exists separately from the usability one beside it.** The sibling assumption "A reader shown the same-id split stops treating those retries as friction" is the risk this candidate is *for*, and it is correctly humans-required. It also says that emitting the label is "the easy half". That is true, but it is still a half, and nothing on the tree checks it. The solution sat in `solutionsMissingInstruments` because its only test was the reader half. This node is the builder's half.

**What the repository says today (read 2026-10-25 via `ost_read_repo`).** `extractFriction` in `src/adapters/transcript.ts` decides a retry with `seenCalls.has(\`${name}:${input}\`)`. The block's `id` is read, but only into `toolById` for matching tool results. It never enters the retry decision, so the split this candidate prints cannot be computed from the event as it is built today. There is also a sign the distinction is real and not hypothetical: the spec's own fixture `assistantTool` gives every call the same id `t1`. So the existing test "reports a repeated identical tool call as a retry" already describes a same-id repeat, and it is filed exactly like a new one.

**How it could be false.** Claude Code may never write the same `tool_use` id twice in one transcript. In that case every repeat is a new call, the split always reads `0 reused`, and the label is noise. That is what the instrument below cannot rule out. A green spec proves the harvester *can* compute the split, not that real transcripts ever contain the case. Settling that takes one grep over real session files for a duplicated `"id":"toolu_` within one file, which is outside `product.repos` and so off this surface.

Unvalidated. Agent-surfaced 2026-10-25 by an unattended sweep; for a human to review.
