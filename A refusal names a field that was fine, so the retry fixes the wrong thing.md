---
type: Opportunity
source: 'TRANSCRIPT:ef6ba23a-db2c-4832-b5e3-aba95040ab8f'
created: '2026-08-20'
evidence: observed
---
#Opportunity #usability #tool-surface #unvalidated #evidence/observed
[[The refusal names the field that failed and the form that would have passed]]

**The need (operator's voice, from the agent's own session):** "I asked for a test with an instrument and a threshold. The tool refused, told me the test 'cannot carry that instrument', and quoted the spec path. So I reworked the instrument. The real cause was that my threshold spelled its number out in words — the one field the message never mentioned."

**What was observed.** `TRANSCRIPT:ef6ba23a-db2c-4832-b5e3-aba95040ab8f` (2026-08-20, unattended sweep): `ost_create_node` tool_error — "Create an opportunity beside an existing sibling with no differentia and require the refusal, then supply one per sibling and require the write" cannot carry that instrument: `test/ost/sibling-differentia-guard.test.ts`… The sweep that hit it recorded, on "A pass that cannot see the repository cannot set an instrument at all" (Issues, 2026-08-20), that the same prose threshold was refused with spelled-out numbers and accepted with digits. The refusal's named subject (the instrument) and its actual trigger (the threshold's number format) were different fields.

**Why it matters.** A refusal is the one sentence a guard gets to send, and on an unattended firing nobody is there to read past it. When it names the wrong field, the guard's protection turns into a turn tax, and worse than a tax: the session's natural repair is to change the field it was told about, which here means swapping a grounded instrument for a guessed one — the exact failure "I overwrote a good instrument because nothing showed me one was already there" records from the other direction. The fix was found by trial, which is what this tree's own corrections ledger exists to stop.

**Litmus (more than one way?):** name the failing field and the form that would pass; check the threshold's format first, with its own message, before the instrument is examined; accept spelled-out numbers; return every problem in one refusal rather than the first one found. Four mechanisms with different trade-offs. Passes.

**Grounding, and its limit.** This pass read `src/mcp/server.ts` and `src/ost/instrument.ts`. The server's schema-level refusals (`validateToolInput`) already list problems per field, so the misdirection is not there; it sits in the tool body in `src/security/tools.ts` (118KB, over the read cap, not read). The exact rule is therefore reported from two observations, not from the code.

**Placement (proposed).** Filed under the bucket about failure signals that do not distinguish their causes; the kinship is that a refusal naming field A when field B failed reads identically to a refusal about field A. A human may prefer it beside "A malformed call lands before anything checks it, and only reading back the file says so", which is the same validation layer failing in the opposite direction.

**Provenance.** One session, recorded mechanically; agent self-observation of the product's own tool. Grounds usability, not demand. n=1.
