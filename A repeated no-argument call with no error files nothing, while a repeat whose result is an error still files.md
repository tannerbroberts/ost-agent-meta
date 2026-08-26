---
type: AssumptionTest
created: '2026-08-26'
evidence: assertion
threshold: >-
  zero friction events from the clean repeat, and >= 1 tool_error from the
  failing repeat
instrument: npx vitest run test/adapters/transcript-retry-inference.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.**

**The assertion contract, so the builder is not handed a blank file.** The subject already exists: `extractFriction`, exported from `src/adapters/transcript.ts` and already exercised by `test/adapters/transcript.test.ts`. The new spec builds two JSONL fixtures by hand and asserts on the returned `FrictionEvent[]`:

1. *The clean repeat.* Two `tool_use` blocks with the same `name` (`mcp__ost-agent__ost_next_work`) and the same `input` (`{}`), and no `tool_result` block carrying `is_error: true` anywhere in the fixture. Expect `extractFriction(jsonl)` to return **no event whose `kind` is `retry`** — under the threshold above, zero friction events from this fixture at all.
2. *The failing repeat, as the positive control.* The same two `tool_use` blocks, plus a `tool_result` block whose `tool_use_id` matches the first call and whose `is_error` is `true`. Expect **at least one event with `kind: "tool_error"`**, proving the edit removed the repeat inference and not the error path with it.

**Why it is red today, and exactly what kind of red.** Stated plainly rather than glossed: the file does not exist, so today the command exits non-zero for a reason that would be identical for any question written on that path. That is the weak red, and it is the only red the instrument grammar permits here — `ost_set_instrument` and `ost_create_node` both refuse a `-t "<case name>"` filter against the existing spec file as shell punctuation, so an instrument cannot name a case inside a file that already passes. The file path is therefore a consequence of the tool surface, not a design choice.

What keeps this from being a blank reservation is that the assertion above is not speculative. Today's `extractFriction` composes `` `${name}:${input}` `` and pushes a `retry` on the second identical signature with no reference to any result, so case 1 is guaranteed to fail on its assertion the moment it is written, against unmodified code. The builder's job is not "create this file"; it is "write these two cases and make case 1 pass without breaking case 2."

**What a green here does not settle.** It proves the edit is surgical on two hand-built fixtures. It does not prove the corpus resembles the fixtures — whether real sessions contain many meaningful repeats carrying no `is_error` is a census over the stored transcripts, and that is how this assumption most plausibly fails. It settles nothing about desirability: a quieter channel is not thereby one anyone wants, and no exit code reaches that question.
