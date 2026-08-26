---
type: AssumptionTest
created: '2026-08-26'
evidence: assertion
threshold: >-
  >= 3 denial fixtures still classified permission_denied with zero uses of
  DENIAL_PATTERNS
instrument: npx vitest run test/adapters/transcript-denial-structure.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.**

**The assertion contract.** Build three JSONL fixtures whose `tool_result` blocks reproduce, verbatim, the three denial shapes `DENIAL_PATTERNS` in `src/adapters/transcript.ts` currently matches — "user doesn't want to proceed", "permission was denied by the user", "user rejected" — each with `is_error: true`, and one control fixture of a genuine tool breakage, also `is_error: true`. Then assert that a classifier which never inspects the result text still returns `permission_denied` for all three denials and `tool_error` for the control.

The spec's job is to make the belief falsifiable by construction: if the only host-written field distinguishing the four fixtures is `is_error: true` — identical across all of them — then no text-blind classifier can pass, and the spec should fail loudly rather than be quietly weakened to read the text after all.

**Why it is red today, and what kind.** The file does not exist, so this is a weak red — it would fail identically for any question written on that path. Recorded honestly, and the reason is the tool surface: the instrument grammar accepts a bare spec path only and refuses a `-t "<case name>"` filter into `test/adapters/transcript.test.ts`, which already passes. What makes the contract more than a reservation is that the current code is strong evidence for the *negative* result: `DENIAL_PATTERNS` is three regexes over English prose, and prose-matching is what gets written when the structured signal is absent. This test is expected to refute its assumption, and that is a good reason to run it early rather than a reason to skip it.

**What a green here does not settle.** It would prove the distinction survives one deletion on four fixtures. It would not touch the candidate's real risk — that the definition of friction now lives in a dependency this project neither controls nor versions — because no run today can see the upstream change that breaks it. Nor does it say whether an operator wants a channel governed by someone else's flag.
