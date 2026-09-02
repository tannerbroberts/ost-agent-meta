---
type: AssumptionTest
source: 'agent-ideation:2026-09-02-unattended-sweep'
created: '2026-09-02'
evidence: assertion
threshold: >-
  zero tool_error events emitted for a marked command, and the identical
  unmarked command still emits one
instrument: npx vitest run test/adapters/transcript-caller-declaration.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.**

Feed `extractFriction` two fixture sessions that differ in exactly one respect: a Bash `tool_use` whose `description` carries the agreed marker, and the same call without it, each followed by a `tool_result` with `is_error: true` and a clean negative body (`Exit code 1` and nothing that diagnoses the command). Assert the marked one yields no `tool_error` and the unmarked one yields exactly one. The pairing is the point — a spec asserting only the marked case would pass on an adapter that had stopped emitting `tool_error` altogether.

**Honest note on the strength of this red, written by the pass that set it.** The named spec does not exist, so the command fails today for a reason it would share with any question anyone wrote on that path — a `no-spec` red, which mints no build permit and hands a builder only "create this file". A stronger form was attempted first and refused: `ost_set_instrument` rejects shell punctuation, so an existing spec plus a quoted `-t` filter naming the missing assertion is not expressible on this surface. What narrows it instead is the paragraph above: the fixture shape, the pairing, and the exact assertion are specified here, so the file is blank but its contents are not undecided. Whoever writes it should get a red on an assertion within one commit, and that is the red worth recording.

**What a green here does NOT settle.** It proves the mechanism can read a mark and act on it. It says nothing about whether any session will write the mark, which is the belief the whole candidate rests on, is a behavioural question no exit code reaches, and is recorded as the solution's kill condition for a person watching a month of transcripts. Feasibility answered mechanically leaves compliance and desirability exactly where they were.
