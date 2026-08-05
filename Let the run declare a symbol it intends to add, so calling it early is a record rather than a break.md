---
type: Solution
source: 'TRANSCRIPT:e335a680-ee48-4171-b8ad-4cfb526e4129'
created: '2026-08-04'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A meaningful share of these failures are dropped intentions rather than wrong names]]

Accept that a run building a feature will reference things it has not written yet, and give that intention somewhere to live. Before calling a not-yet-existing symbol, the run declares it — name, module, shape — and the declaration is held open until the definition lands. A batch that ends with declarations still open reports them, by name, as the work it did not finish.

**Shape.** A small ledger, not a code generator. It writes no stubs and changes no source; it records `ToolContext.configProblem — intended, not yet defined` and complains at the end of the batch if it is still intended.

**What it is actually for.** Not catching mistakes — catching *abandonment*. The `configProblem` capture is a run that meant to add a property and referenced it first; had the batch ended there, nothing would have said the intention was dropped except a typecheck error that reads identically to a typo. This option is the only one of the three that distinguishes "I meant to do this and did not" from "I got the name wrong".

**Against the alternatives.** Weakest on the misspelling case — a run that declares `reconcileWithUsage` believing it exists gets no objection, because declaring is exactly what it would do. So this does not replace either sibling; it covers the half of the need they do not.

**Honest doubt about whether to build it at all.** It requires the run to volunteer the declaration, and every mechanism that depends on the agent remembering an extra step is one the tree should be sceptical of. If the census beneath this opportunity shows the misspelling case dominates and the dropped-intention case is rare, this should be deferred rather than built.

## Test

[[Count how many of the captured failures were a dropped intention rather than a wrong name]]

`npx vitest run test/telemetry/symbol-failure-census.test.ts`

Green when at least 3 in 10 captured symbol failures are dropped-intention rather than wrong-name. Below that bar this solution should be deferred in favour of its two siblings — the census is placed to be able to kill this node, and that is deliberate.

## History
- 2026-08-05 unlinked [[Count how many of the captured failures were a dropped intention rather than a wrong name]] — moved under [[A meaningful share of these failures are dropped intentions rather than wrong names]] — the belief this test measures now has a node of its own
