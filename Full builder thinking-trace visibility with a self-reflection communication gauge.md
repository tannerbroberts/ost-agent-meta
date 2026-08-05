---
type: Solution
status: unvalidated
source: 'human:conversation:2026-07-26'
created: '2026-07-26'
---
#Solution #unvalidated #founder-provided #evidence/assertion
[[Do the three reflection questions catch a builder misunderstanding the pass output missed]]

**Mechanism (founder-provided, 2026-07-26):** When the builder is an AI agent — as in the OST-Agent's own OST — the builder's thinking trace is completely visible to the OST-Agent. The OST-Agent then gauges its own communication to the builder via self-reflection questions asked against that trace:

1. Does the builder understand exactly what to build and why?
2. Does it understand the working environment?
3. Are there further constraints that only a human can unblock?

**Closing the loop:** To that end, the OST-Agent's OST should actually be able to alter the loops that run the ideation and building — what the gauge learns about communication failures becomes changes to the running loops, not just annotations.

**Contrast with neighbors:** [[Adopt session transcripts as the trace source instead of new instrumentation]] is a trace-*acquisition* mechanism serving the usage-feed opportunity; this node *consumes* trace visibility to audit whether the OST-Agent's own instructions landed, and routes the verdicts into loop control. [[Agent proposes its own workflow changes for one-click adoption]] is the nearest existing loop-alteration mechanism — human-adopted proposals; this solution implies a tighter coupling where the OST itself can alter the running loops. A human should decide how much of that authority to grant.

**Key assumptions (explicit, untested):** (feasibility) the builder's full thinking trace is actually accessible to the OST-Agent; (usability) the three reflection questions, asked against a real trace, surface misunderstandings the pass output alone does not; (viability/safety) letting the tree alter its own ideation/build loops improves route efficiency without eroding the append-only trust guarantees; (desirability) the founder and future operators want loop authority to live in the tree rather than with the human.

**Rung honesty:** founder-provided solution, entered unvalidated — no promotion implied by its provenance.

## Definition of done

[[Do the three reflection questions catch a builder misunderstanding the pass output missed]]

```
npx vitest run test/skill/reflection-questions.test.ts
```

Green means: all three reflection questions reach every pass output, each bound to a named node in that pass rather than asked in the abstract. Green does **not** mean they catch anything — a real builder misreading a real pass output is the measurement, and that stays with a human.
