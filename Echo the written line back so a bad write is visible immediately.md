---
type: Solution
source: 'agent-ideation:2026-07-26-tenth-pass'
created: '2026-07-26'
evidence: assertion
---
#Solution #evidence/assertion
[[Does an operator notice a bad write when the tool echoes the line back]]

**The idea.** A mutating tool returns the line it actually wrote, not a confirmation that it wrote something. `annotated "Some node"` becomes `annotated "Some node": - 2026-07-26 undefined`.

**Why this one is interesting despite being the weakest.** It is the only candidate here that would have surfaced the defect **at the moment it happened, to the party that caused it**, with no rule and no schema — the caller reads its own output and sees the word `undefined` in it. The other two prevent this specific failure; this one shortens the distance between *any* bad write and its discovery, including failures nobody has predicted.

**Prior art in this codebase, and it works.** `ost-agent lane --set` already returns the exact History line it appended, and `ost-agent result` prints the recorded line plus its uncovered clause. Those surfaces have never produced a silent bad write. `ost_annotate` returned `annotated "<title>"` — a confirmation that the call completed, which is precisely the thing that was true.

**Where it fails.** It relies on somebody reading the output. An unattended pass discards tool output routinely — this pass would very likely have skimmed past it — so as a sole defence it is weak. As a *third* layer behind a schema check and a write guard, it is nearly free.

⚠️ Unvalidated. Agent-ideated.

## Definition of done

[[Does an operator notice a bad write when the tool echoes the line back]]

`npx vitest run test/mcp/echo-written-line.test.ts`

Every mutating tool must return the line it actually wrote, not a confirmation that it wrote something.

**Red against today's code, and this pass observed it directly rather than inferring it.** `ost_set_instrument` already echoes its whole History line — the prior art this node cites, and it works. But `ost_annotate` still returns `annotated "<title>"`, `ost_append_to_node` returns `appended to "<title>"`, and `ost_create_node` and `ost_link_nodes` report only that the call completed. Four surfaces on which the original defect — a write containing the word `undefined`, confirmed as successful — is still expressible today.

**What a green here does not settle, and the node is honest that it is fatal on its own.** It relies on somebody reading the output. An unattended pass discards tool output routinely; this pass read hundreds of tool results and would have skimmed past a bad line in most of them. Whether an operator *notices* is the humans-required test. The node's own conclusion stands: this is nearly free as a third layer behind a schema check and a write guard, and weak as a sole defence.
