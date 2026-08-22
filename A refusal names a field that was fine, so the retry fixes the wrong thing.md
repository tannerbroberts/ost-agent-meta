---
type: Opportunity
source: 'TRANSCRIPT:ef6ba23a-db2c-4832-b5e3-aba95040ab8f'
created: '2026-08-20'
evidence: observed
---
#Opportunity #usability #tool-surface #unvalidated #evidence/observed
[[The refusal names the field that failed and the form that would have passed]]
[[Drop the create-time numeric-bar check for no-spec instruments and let verify-time catch the missing bar]]
[[Express the threshold rule as a schema pattern, so the server's existing per-field validator reports it]]

**The need (operator's voice, from the agent's own session):** "I asked for a test with an instrument and a threshold. The tool refused, told me the test 'cannot carry that instrument', and quoted the spec path. So I reworked the instrument. The real cause was that my threshold spelled its number out in words — the one field the message never mentioned."

**What was observed.** `TRANSCRIPT:ef6ba23a-db2c-4832-b5e3-aba95040ab8f` (2026-08-20, unattended sweep): `ost_create_node` tool_error — "Create an opportunity beside an existing sibling with no differentia and require the refusal, then supply one per sibling and require the write" cannot carry that instrument: `test/ost/sibling-differentia-guard.test.ts`… The sweep that hit it recorded, on "A pass that cannot see the repository cannot set an instrument at all" (Issues, 2026-08-20), that the same prose threshold was refused with spelled-out numbers and accepted with digits. The refusal's named subject (the instrument) and its actual trigger (the threshold's number format) were different fields.

**Why it matters.** A refusal is the one sentence a guard gets to send, and on an unattended firing nobody is there to read past it. When it names the wrong field, the guard's protection turns into a turn tax, and worse than a tax: the session's natural repair is to change the field it was told about, which here means swapping a grounded instrument for a guessed one — the exact failure "I overwrote a good instrument because nothing showed me one was already there" records from the other direction. The fix was found by trial, which is what this tree's own corrections ledger exists to stop.

**Litmus (more than one way?):** name the failing field and the form that would pass; check the threshold's format first, with its own message, before the instrument is examined; accept spelled-out numbers; return every problem in one refusal rather than the first one found. Four mechanisms with different trade-offs. Passes.

**Grounding, and its limit.** This pass read `src/mcp/server.ts` and `src/ost/instrument.ts`. The server's schema-level refusals (`validateToolInput`) already list problems per field, so the misdirection is not there; it sits in the tool body in `src/security/tools.ts` (118KB, over the read cap, not read). The exact rule is therefore reported from two observations, not from the code.

**Placement (proposed).** Filed under the bucket about failure signals that do not distinguish their causes; the kinship is that a refusal naming field A when field B failed reads identically to a refusal about field A. A human may prefer it beside "A malformed call lands before anything checks it, and only reading back the file says so", which is the same validation layer failing in the opposite direction.

**Provenance.** One session, recorded mechanically; agent self-observation of the product's own tool. Grounds usability, not demand. n=1.

## Second observed instance — a different field pair, and it generalises the mechanism (unattended sweep, 2026-08-22)

This node closed at n=1 and said so. Here is n=2, from a different tool, a different field pair, and a different session — which matters because the first instance could be read as one quirk of the threshold checker, and two instances in different code paths cannot.

**What was observed.** `TRANSCRIPT:14f184b4-6ca1-41d3-bf1f-b9e036b2a1a0` (2026-08-21, unattended sweep) shows three consecutive `ost_set_instrument` refusals against one node, "Have someone with the vault-write code open confirm every commit path can carry a session id without breaking commit-message parsers":

1. `cannot set that instrument on "…": "npx vitest run test/git/commit-provenance.test.ts -t …` — a grammar refusal about the command string.
2. The same refusal again, after a rework of the same field.
3. `refusing to instrument "…": it is labelled humans-required, so a person is the measurement…`

**Why it is this need and not a new one.** The first two refusals named a field the session could fix, and it did fix it, twice. The third named a condition no rework of that field could ever satisfy: the node was labelled humans-required and could not carry any instrument at all. The session spent three calls to learn something the first refusal could have said. That is the same defect as the threshold/instrument pair already recorded above — the message names a satisfiable objection while an unsatisfiable one is also true — and it is already inside this node's own litmus list, as "return every problem in one refusal rather than the first one found."

**What is new, and worth a builder's attention.** The first instance is a *misnaming* (field A reported, field B at fault). This one is an *ordering* (both objections real, the cheap one reported first). They call for different repairs from the same litmus: misnaming wants the refusal to name the right field; ordering wants the checks sorted so a terminal condition is reported before a fixable one, or all problems returned at once. A builder taking only "name the failing field" would fix the first instance and leave this one intact, because here the field named was genuinely failing.

**A caution against over-reading.** Both instances are the agent observing its own use of its own product; neither is outside-user data. This raises the count and the mechanism's generality, not the rung.

_Source: `TRANSCRIPT:14f184b4-6ca1-41d3-bf1f-b9e036b2a1a0`, read in full this pass. Observed behavior captured mechanically from the agent's own session transcript. Grounds usability, not demand. Node's rung unchanged at `observed`; n=1 → n=2._
