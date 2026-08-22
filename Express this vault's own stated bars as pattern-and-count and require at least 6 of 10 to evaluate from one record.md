---
type: AssumptionTest
source: 'agent-ideation:2026-08-21-unattended-sweep'
created: '2026-08-22'
evidence: assertion
threshold: >-
  Of the 10 pre-committed bars sampled from this vault, at least 6 must evaluate
  to a verdict from a single record's text alone, and 0 may require a model
  call. Fewer than 6 refutes the assumption and closes the ingest-time
  candidate.
instrument: npx vitest run test/evidence/ingest-bar-tripwire.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**Pre-committed threshold, fixed before the spec is written:** take the 10 bars this vault has actually stated (the `**Pre-committed threshold**` and `**A pre-committed bar**` paragraphs already on its nodes), encode each as a pattern, a count and a comparison, and feed each one a single record. **At least 6 of the 10 must return a verdict — breached or not-breached — from that one record's text alone, and 0 may need a model call.** Below 6, the assumption is refuted and the ingest-time candidate is closed rather than reworked, because a tripwire that can express a minority of bars leaves an unflagged claim exactly as untrustworthy as it is today.

The two failure kinds are counted separately and reported, because they argue for different things: a bar needing **several records** (a corpus statistic) says move the check to a sweep, and a bar needing **judgement about content** says this class of bar is not mechanisable anywhere.

**What the spec asserts.** `test/evidence/ingest-bar-tripwire.test.ts` holds the 10 encoded bars as a fixture alongside one real record each, drives the evaluator, and asserts the 6-of-10 floor and the zero-model-calls property. It is red today because no evaluator exists: `src/adapters/` has no bar-matching path, and `ost_ingest_inbox` reports capture counts per channel and nothing else.

**Read this before treating the red as strong.** This is a **no-spec red** and the tree should say so rather than let it pass for an assertion-specific one. The file named does not exist and this surface cannot author it, so today the command fails for the same reason it would fail for any question written on that path. What makes it worth setting anyway is the threshold above: per `src/eval/buildable.ts`, a `no-spec` run keeps its permit when the threshold is bound, and a builder can work to "6 of 10, 0 model calls" without this pass having written a line of the spec. The mechanism that is absent is named above so the builder is not left guessing which module to open.

**What a green here does not settle.** That the bars are mechanisable says nothing about whether tripping on them at ingest catches the staleness that actually occurs — that is the sibling assumption beneath this same solution, and it is a person's classification of past stale claims, not a spec. A passing count here plus a failing answer there means this candidate is buildable and pointless, and the two must be read together.
