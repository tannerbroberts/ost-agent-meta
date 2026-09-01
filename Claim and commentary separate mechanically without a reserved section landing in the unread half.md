---
type: Assumption
source: 'agent-ideation:2026-08-31-unattended-sweep'
created: '2026-09-01'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion
[[A reserved section written under a dated heading is served in the claim half, not the commentary half]]

**The belief, stated so it could be false:** a node's body can be split into a claim region and a commentary region by a rule with no judgement in it, and a reserved section — `## Results`, `## Uncovered`, `## Instrument Log` — always lands in the claim region, never in the commentary region a default read does not return.

**Risk category: feasibility**, and it is answerable from the repository rather than from anybody's afternoon, which is why this assumption exists separately from the fidelity one beside it.

**What grounds it, read first-party this pass.** `src/mcp/node-body.ts` already performs a two-way split: `splitReservedSections` (from `src/ost/sections.ts`) divides a body into `prose` and labelled `reserved` blocks, and the module's own header states why — a caller reading a reserved block inline with prose "could carry one into composed text, which is authoring a measurement by quotation." So the candidate above is not inventing a separation; it is adding a third region to one that exists and is already safety-critical.

**Why it might be false.** The existing split is by heading, against a fixed list of reserved headings. Commentary carries no such list — it arrives as dated `## ` sections with arbitrary titles, and the boundary between "the claim's own reasoning, in a `## ` section" and "a pass's note about the claim" is not a property of the heading. A rule that guesses from the date prefix would put a reserved section written under a dated heading on the wrong side, and that is the failure that matters: a human's recorded result silently absent from every default read is functionally a revoked permit, which this product's strongest guarantee says no tool may produce.

**A second reason it might be false, from the same read.** `nodeBody` truncates `prose` at `MAX_BODY_CHARS` and reports the shortfall in `truncated`. The 30,395-character node this pass read came back with `truncated: []`, so the cap did not bite — meaning the existing bound is set above the sizes actually occurring and is not currently protecting any reader. A split scheme that assumes the cap is doing work would be building on something inert.

Unvalidated. Agent-surfaced 2026-08-31 from a first-party read of `src/mcp/node-body.ts`.
