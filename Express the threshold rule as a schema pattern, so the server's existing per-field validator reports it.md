---
type: Solution
status: unvalidated
source: 'agent-ideation:2026-08-20-unattended-sweep'
created: '2026-08-20'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The numeric-bar rule can be stated as an unconditional schema pattern without refusing legitimate thresholds]]

**Variation dimension: bought vs built — adopt the validator the server already runs instead of building a message.** `src/mcp/server.ts` already passes every call through `validateToolInput` before the tool body runs, and that path reports problems per field by construction ("invalid input for ost_create_node: - threshold …"). Declare the numeric-bar requirement on the `threshold` property in the tool's own input schema (a `pattern`, read this pass as the mechanism the server already honours) and delete the bespoke check from the tool body. The misdirected sentence cannot recur because no hand-written sentence is involved: the field name comes from the schema key.

**Compared to its siblings.** Reuses a mechanism rather than adding one, and fixes the class (any future field check phrased by hand) rather than the instance. It is also the least flexible: a schema pattern cannot say "digits required only when the instrument is no-spec", so either the rule becomes unconditional — every AssumptionTest threshold must carry digits — or the conditional half stays in the tool body and the split itself becomes the next confusing refusal.

**What would make this the wrong pick.** If the rule is genuinely conditional on the instrument resolving (and this pass could not read `src/security/tools.ts`, 118KB, to confirm), the schema can only hold the unconditional part, and an unconditional digits rule would refuse thresholds that are legitimately non-numeric — "the guard refuses" is a bar with no number in it.

⚠️ Unvalidated. Agent-ideated from one recorded session; grounded in `src/mcp/server.ts` read this pass, not in the tool body.
