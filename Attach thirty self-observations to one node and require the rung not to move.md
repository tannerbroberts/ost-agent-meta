---
type: AssumptionTest
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
threshold: >-
  After attaching 30 transcript records from the same actor to one opportunity,
  its rung is unchanged and every surface reporting its source count also
  reports the distinct-actor count — 0 places where the raw count appears alone.
instrument: npx vitest run test/adapters/corroboration-actor-ceiling.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Who runs it.** An attended session with a build environment, or a human. This pass could not set a lane label — that is a human's `ost-agent lane --set`.

**What this measures.** Attach thirty `TRANSCRIPT:` records, all from the same actor, to one opportunity. Assert the node's evidence rung is exactly what it was. Then walk every surface that prints a source count — the rollup's per-bucket line, `status`, the node's own frontmatter — and assert none of them shows the raw number without the distinct-actor number beside it.

**The bar, pre-committed.** Rung unchanged, and zero surfaces printing a bare count. The second half is the real bar: a ceiling that holds internally while the headline number a human skims says "40 sources" has failed at the only thing it was for.

**Why it is red today.** There is no way to attach an evidence record to an existing node at all — the 65 records in this pass's queue had exactly two possible dispositions, create a node or leave them. So the spec fails on its first line, against a missing mechanism rather than a missing file. The actor-count assertions fail for a second, independent reason: the rollup's per-bucket line reports "N source(s)" with no actor breakdown today, which this pass read directly.

**What a green run does NOT settle.** It shows the count cannot be inflated mechanically. It does not show that attaching is the *right* disposition for these records — whether a friction record genuinely corroborates the opportunity someone attached it to is a judgement, made 65 times by the agent whose queue is being drained, and no spec inspects it. It also says nothing about desirability: nobody has said they want recurrence to strengthen a node rather than simply to stop bothering them.

## History
- 2026-08-06 body edited — The body declared "Lane: compute-only", which this pass had no power to set — `ost_flag_humans_required` is withheld on this surface and only a human's `ost-agent lane --set` moves what compute may run. The node carries no `lane:` field, so its effective lane is needs-humans (confirmed: it landed in `assumptionWork.needsHumans`), and the prose contradicted that. Replaced with the vault's established "Who runs it" phrasing.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/adapters/corroboration-actor-ceiling.test.ts` — No test files found, exiting with code 1
