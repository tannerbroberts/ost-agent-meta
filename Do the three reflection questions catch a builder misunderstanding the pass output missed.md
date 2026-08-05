---
type: AssumptionTest
status: unvalidated
source: 'human:conversation:2026-07-26'
created: '2026-07-26'
evidence: assertion
instrument: npx vitest run test/skill/reflection-questions.test.ts
---
#AssumptionTest #unvalidated #usability #evidence/assertion

**Assumption under test (usability — the riskiest):** asking "Does the builder understand exactly what to build and why? Does it understand the working environment? Are there constraints only a human can unblock?" against a builder's full thinking trace surfaces real misunderstandings that the builder's own output does not reveal.

**Proposed test (small, fast — human runs it):** Take the thinking traces from three recent bootstrap-loop builder sessions that already exist. For each, a reader (human or a fresh model instance with no stake in the session) answers the three questions from the trace alone, then compares against what the session actually shipped and reported.

**Pre-committed success threshold:** in at least one of the three sessions, the questions surface a concrete misunderstanding — wrong target, wrong environment assumption, or a human-only blocker the builder worked around silently — that the session's own report did not disclose. Zero out of three means the gauge adds no signal over existing output and the solution's core premise fails cheap.

**Why this one first:** feasibility (trace access) is already partially evidenced — session transcripts exist and [[Adopt session transcripts as the trace source instead of new instrumentation]] names the mechanism. The untested leap is that reflective questioning of a trace yields actionable communication verdicts. If it does not, loop-alteration authority is moot.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/skill/reflection-questions.test.ts — The three questions cannot catch anything they are never asked. This asserts they are asked and are answerable: every pass output carries all three reflection questions, each is bound to a named node in that pass rather than asked in the abstract, and an output that omits one or asks it unbound fails. Missing-spec red, not assertion red — the gauge is not built, so the command fails on a missing file; a builder should write it against the real skill-output renderer so it goes red on the missing question instead. It does not settle whether the questions CATCH a misunderstanding: that needs a real builder misreading a real pass output, which is a person's behaviour and stays with a human.
