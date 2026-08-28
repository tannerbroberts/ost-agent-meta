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

**Lane: not this pass's to declare.** The test carries an instrument and could in principle be settled by one command, but granting compute permission to run it is a human's call (`ost-agent lane --set`); this sweep holds no tool that can make it, so the test sits in the needs-a-person lane until someone decides otherwise.

**The assertion contract, so the builder is not handed a blank file.** The subject already exists: `extractFriction`, exported from `src/adapters/transcript.ts` and already exercised by `test/adapters/transcript.test.ts`. The new spec builds two JSONL fixtures by hand and asserts on the returned `FrictionEvent[]`:

1. *The clean repeat.* Two `tool_use` blocks with the same `name` (`mcp__ost-agent__ost_next_work`) and the same `input` (`{}`), and no `tool_result` block carrying `is_error: true` anywhere in the fixture. Expect `extractFriction(jsonl)` to return **no event whose `kind` is `retry`** — under the threshold above, zero friction events from this fixture at all.
2. *The failing repeat, as the positive control.* The same two `tool_use` blocks, plus a `tool_result` block whose `tool_use_id` matches the first call and whose `is_error` is `true`. Expect **at least one event with `kind: "tool_error"`**, proving the edit removed the repeat inference and not the error path with it.

**Why it is red today, and exactly what kind of red.** Stated plainly rather than glossed: the file does not exist, so today the command exits non-zero for a reason that would be identical for any question written on that path. That is the weak red, and it is the only red the instrument grammar permits here — `ost_set_instrument` and `ost_create_node` both refuse a `-t "<case name>"` filter against the existing spec file as shell punctuation, so an instrument cannot name a case inside a file that already passes. The file path is therefore a consequence of the tool surface, not a design choice.

What keeps this from being a blank reservation is that the assertion above is not speculative. Today's `extractFriction` composes `` `${name}:${input}` `` and pushes a `retry` on the second identical signature with no reference to any result, so case 1 is guaranteed to fail on its assertion the moment it is written, against unmodified code. The builder's job is not "create this file"; it is "write these two cases and make case 1 pass without breaking case 2."

**What a green here does not settle.** It proves the edit is surgical on two hand-built fixtures. It does not prove the corpus resembles the fixtures — whether real sessions contain many meaningful repeats carrying no `is_error` is a census over the stored transcripts, and that is how this assumption most plausibly fails. It settles nothing about desirability: a quieter channel is not thereby one anyone wants, and no exit code reaches that question.

## History
- 2026-08-26 body edited — Created with a prose line reading "**Lane: compute-only.**", which this pass had no authority to declare and which the sweep immediately contradicted — the test came back under `assumptionWork.needsHumans`, since setting the permissive lane is a human's `ost-agent lane --set` and no agent surface can grant it. A prose lane that disagrees with the `lane:` field is a check violation (lane-conflict) and, worse, tells a reader compute may run this unattended when nothing has said so. Replacing the declaration with an accurate note about who decides. No other claim changed.

## The census this node defers now has a named deterministic generator (2026-08-28)

This node's closing paragraph says a green here would not prove the corpus resembles the fixtures, and names the open question: whether real sessions contain many meaningful repeats carrying no `is_error`. One fact about that census is now established first-party and is recorded here because it changes the expected answer.

There is at least one generator of no-error repeats that fires by construction rather than by chance: the unattended loop's own prescribed opening and closing steps. `ost_ingest_inbox` and `ost_next_work` both take no arguments, so every call of either has the identical signature `{}` under `extractFriction`'s `` `${name}:${JSON.stringify(input)}` ``, and the loop's prompt instructs a pass to call both at step 1 and again at step 5. The second pair trips the repeat detector every time. The 2026-08-28 sweep captured a record consisting of exactly those two events and nothing else — `TRANSCRIPT:6d96802b-a693-425d-97c4-3eb0db903f94` — and the fuller write-up sits on the candidate this test hangs beneath, "A human-edited manifest of loop-prescribed call sequences the harvester suppresses", rather than being restated here.

**What it means for this test specifically.** Fixture case 1 is not a hypothetical shape. It is a transcription of what every well-behaved firing produces, which raises this test's value: the behaviour it pins is the one the corpus exercises most. It does not lower the bar or change either assertion, and it does not settle the census — the share of the 441 unmapped records that are of this kind is still unmeasured, and the share is what decides whether suppression is worth building.

_Source: first-party read of `src/adapters/transcript.ts` via `ost_read_repo`, plus this sweep's own ingest output. No test was run and no result is recorded; the instrument above is still red and still uncleared._
