---
type: AssumptionTest
source: 'agent-ideation:2026-09-02-unattended-sweep'
created: '2026-09-02'
evidence: assertion
threshold: >-
  all six diagnostic bodies classify as tool_error and all six clean-negative
  bodies as observation, with zero crossovers
instrument: npx vitest run test/adapters/friction-negative-answer.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.**

Twelve fixture `tool_result` bodies, every one carrying `is_error: true`, split into two groups of six drawn from shapes this vault's own records actually contain.

*Clean negatives, which must classify as `observation`:* a grep miss; `Exit code 1 … Tests 3 failed | 7 passed (10)`; a `diff` reporting differences; a `gh pr checks` reporting a pending check; a search printing matched lines with exit 1; an empty body with only the exit-code line.

*Diagnoses of the command, which must stay `tool_error`:* `(eval):1: == not found`; `command not found`; a Node `Traceback`/stack; a `usage:` line from a mis-flagged invocation; a TypeScript compile error; a permissions refusal that is not one of the `DENIAL_PATTERNS`.

Zero crossovers in either direction. The two-sided threshold is the point: a demoter that returns `observation` for everything satisfies any one-sided bar and destroys the channel.

**Honest note on the strength of this red, written by the pass that set it.** The named spec does not exist, so today's failure is a `no-spec` one — the same failure any question written on that path would produce, minting no build permit. A sharper form was attempted and refused: this surface will not accept shell punctuation in an instrument, so an existing spec plus a quoted `-t` naming the missing assertion cannot be expressed. The twelve fixtures above are the compensation — the file is unwritten but not undesigned, and the first commit against it should produce a red on an assertion.

**What a green here does NOT settle.** It proves a pattern separates twelve bodies somebody chose, which is a claim about the fixtures as much as about the rule. It says nothing about the rate on the real corpus, nothing about whether the host clipped a diagnostic out of a long result before the adapter ever saw it, and nothing about whether anyone reading the channel finds the `observation` kind useful. The corpus rate is the solution's kill condition and belongs to a person with fifty hand-labelled records.

## Instrument Log
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/adapters/friction-negative-answer.test.ts` — test/adapters/friction-negative-answer.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/adapters/friction-negative-answer.test.ts` — test/adapters/friction-negative-answer.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/adapters/friction-negative-answer.test.ts` — test/adapters/friction-negative-answer.test.ts does not exist — no spec was collected, so nothing was measured
