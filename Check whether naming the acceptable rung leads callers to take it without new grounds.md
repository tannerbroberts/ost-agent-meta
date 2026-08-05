---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: At most 5 of 20 retries take the suggested value with no new grounds cited.
instrument: npx vitest run test/telemetry/rung-suggestion-reflex.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that a suggestion informs rather than substitutes for judgement. A rung refusal that names the ceiling is one keystroke from a caller declaring the ceiling reflexively — the ladder climbed by autocomplete rather than by evidence.

**Risk category: usability.**

**Design.** Add the suggestion to rung refusals only. Over the following twenty refused calls, record what the caller declared next and whether their retry cited any grounds it had not cited before. A caller that simply takes the named value with no new justification is the failure this is looking for.

**Why it is small.** One message change, and the traces already record every call and its arguments.

**What it will not cover.** Taking the named ceiling is often correct — it may be the honest rung. Distinguishing a reflexive acceptance from a correct one requires reading the justification, which is a judgement, so the count is a flag rather than a verdict.

A human reads the retries and records the result.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/telemetry/rung-suggestion-reflex.test.ts — The node says the data needed is already captured — "the traces already record every call and its arguments" — and its bar is one count: at most 5 of 20 retries take the suggested value with no new grounds cited. The spec walks the recorded tool-invocation trace for refused `ost_set_evidence` and `ost_create_node` calls that named a ceiling, pairs each with the caller's next declaration on the same node, and counts the retries that adopt the named rung while the justification text is unchanged from the refused attempt, asserting that count against the 5-of-20 bar. It fails today for two compounding reasons: the refusal does not name the acceptable ceiling yet, so no suggestion exists to be taken reflexively, and nothing in the repository pairs a refused call with the retry that followed it — the trace stores calls, not call sequences. What it does not settle is the thing the node is careful about, and the command must not be read past it: taking the named ceiling is often correct, because it may be the honest rung, and separating a reflexive acceptance from a right one means reading the justification. This produces the flag, never the verdict.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/telemetry/rung-suggestion-reflex.test.ts` — No test files found, exiting with code 1
