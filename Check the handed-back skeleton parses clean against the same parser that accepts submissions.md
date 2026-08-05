---
type: AssumptionTest
created: '2026-08-05'
evidence: assertion
threshold: >-
  The skeleton parses clean against the submission parser, and a drift check
  fails if the two ever diverge.
instrument: npx vitest run test/skill/skeleton-validity.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**The assumption: the skeleton stays legal.** A starting template is only worth having if it is valid against the parser that will judge the finished artifact, and it has to stay valid as that parser changes. The node names the failure directly — a stale skeleton is worse than none, because it teaches a dialect the surface has moved off, confidently.

**Risk category: feasibility.**

**Design.** Parse the handed-back skeleton with the same parser that accepts submissions and assert it is clean. Add a drift assertion that fails if the skeleton and the parser diverge, so staleness is caught by the suite rather than by a composer. Assert the skeleton includes one example of each construct the grammar permits, since a skeleton that shows only a subset silently narrows what gets built.

**Why it is small.** One artifact, one parse, one drift check — the same pattern the project already uses to keep its generated skill from going stale.

**What it does NOT cover.** The scope limitation, which is this candidate's real weakness. A skeleton constrains the parts it shows and says nothing about the parts it does not, so a composer extending past the example is guessing again — which is exactly what a hundred-and-seventy-line artifact does. Nor can a spec see whether templates calcify structure: composers staying near the starting shape is a behavioural claim, and buying dialect-correctness with a narrowed range of artifacts would look identical to success from inside the suite.
