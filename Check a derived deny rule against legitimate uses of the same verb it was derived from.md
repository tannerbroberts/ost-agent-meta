---
type: AssumptionTest
created: '2026-08-05'
evidence: assertion
threshold: >-
  Zero false refusals across the corpus of legitimate uses, and every derived
  rule is attributed to the refusal it came from and reversible by one human
  action.
instrument: npx vitest run test/security/derived-deny-rule.test.ts
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**The assumption: a rule inferred from one refusal can be narrow enough not to eat legitimate work.** This is the candidate's whole risk. A deny rule derived from `sleep`-before-poll must not refuse a `sleep` in a fixture that needs a real delay, and the class the guard infers must not be wider than the class that was actually wrong.

**Risk category: feasibility, with a governance clause that is not optional.**

**Design.** Build a corpus of uses of the same verb that are legitimate. Derive a deny rule from the observed `sleep 45 && gh pr checks` refusal and run the corpus past it. Any legitimate use refused is a failure, not a tuning note. Separately assert every derived rule records which refusal produced it and can be reversed by one human action.

**Why it is small.** One rule, one corpus, no live sessions.

**What it does NOT cover.** The asymmetry that makes this candidate dangerous is only partly mechanical. A spec can count false refusals on a corpus someone thought to assemble; it cannot find the capability nobody realised was lost, because that one is absent from the corpus by definition. It also says nothing about the deeper worry already named in this tree as "The agent narrows its own capability to get past a gate I set" — an agent deriving its own constraints is doing that by design here, and whether that is acceptable is a human's call, not a suite's.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/security/derived-deny-rule.test.ts` — No test files found, exiting with code 1
- 2026-09-02 **green** (exit 0) `npx vitest run test/security/derived-deny-rule.test.ts` — Duration  257ms (transform 36ms, setup 0ms, collect 40ms, tests 17ms, environment 0ms, prepare 36ms) [spec bfab6446c445]
