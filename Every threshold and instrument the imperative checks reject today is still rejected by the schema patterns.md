---
type: AssumptionTest
source: 'agent-ideation:2026-08-30-unattended-sweep'
created: '2026-08-30'
evidence: assertion
threshold: >-
  exactly 0 inputs rejected by the imperative check become accepted by the
  pattern, across at least 12 cases
instrument: npx vitest run test/mcp/schema-pattern-parity.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** A differential test over two pure predicates — no vault, no transport, no person.

**What the spec must assert.** This is a parity test, not a feature test, and it should be written as one: assemble a corpus of threshold strings and instrument strings, run each through both the current imperative check and the candidate `pattern`, and compare verdicts.

1. **The direction that matters: exactly 0 inputs rejected by the imperative check are accepted by the pattern.** A pattern written to admit everything currently valid will tend to admit some currently-invalid input too, and that widening is silent — a threshold nobody can read as a bar gets written, restoring the exact failure the check exists to prevent.
2. The reverse direction is reported but not required to be zero: a pattern that rejects something the imperative check allowed is a tightening, which is safe and merely inconvenient, and the spec should print those cases rather than fail on them.
3. The corpus must include the real refusals this tree has already collected, not invented ones — the restated-sentence thresholds the write-time check turns away, and the `-t` filtered instrument forms from sessions `fe8409a0` and `14f184b4`. A parity test over cases the author chose is a test of the author's imagination.
4. A positive control: at least one input both sides accept, so a pattern that rejects everything cannot pass vacuously.

**Assertion 4 is not decoration.** A parity test whose only requirement is "the pattern rejects everything the checks reject" is trivially satisfied by a pattern matching nothing, and that is the failure a builder under time pressure would ship.

**Why it fails today, stated honestly.** `test/mcp/schema-pattern-parity.test.ts` does not exist, so this run files as `no-spec` and mints no permit. This is the weak red form. It is worth noting that this is the one of the three tests that could most nearly have been strong: both predicates it compares are pure functions, so a builder can write it against `src/knowledge/instruments.ts` as it stands today and watch it fail only on the pattern half.

**What a green would NOT settle.** Message quality — the whole reason the parent candidate is a trade rather than a win. A pattern violation renders as "must match pattern", where the current message explains what a threshold is for; parity of verdicts says nothing about parity of usefulness. It also leaves the tree-dependent checks untouched by construction, so a caller whose call is both malformed and disqualified still pays two turns.
