---
type: AssumptionTest
source: 'agent-ideation:2026-09-02-unattended-sweep'
created: '2026-09-02'
evidence: assertion
threshold: >-
  5 of 5 well-formed bodies yield the correct number, 2 of 2 malformed yield
  null, and zero bodies yield a wrong number
instrument: npx vitest run test/adapters/friction-exit-code.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.**

Seven fixture Bash `tool_result` bodies through `extractFriction`, asserting a new `exitCode` field on the emitted `FrictionEvent`.

*Five well-formed:* `Exit code 1` alone; `Exit code 2` followed by a diagnostic; `Exit code 1` followed by matched grep lines; a vitest summary with `Exit code 1`; and a body where the same digits appear again later in the output, so a naive first-number match would pick the wrong one.

*Two malformed:* a body with no exit-code line at all, and one where the phrase appears inside quoted content rather than as the host's own header. Both must yield `null`, not a guess. Returning `null` is the load-bearing half — a parser that guesses on a body it cannot read hands the lookup table a confident wrong row, and a wrong row is a mis-file with no trace, which is strictly worse than the mis-file this whole branch exists to remove.

The event must also carry the invoked tool's name, since a contract cannot be looked up without knowing whose contract it is.

**Honest note on the strength of this red, written by the pass that set it.** The named spec does not exist, so today's red is a `no-spec` red and mints no build permit. It is the weakest kind of failure and it is what this surface permits: `ost_set_instrument` refuses shell punctuation, so an existing spec plus a quoted `-t` filter naming the missing assertion — the sharper form — cannot be written here. The seven fixtures and the null requirement are the design the first commit should turn into an assertion-level red.

**What a green here does NOT settle.** It proves a number can be recovered from bodies of the shapes chosen above. It does not establish that the recovered number belongs to the tool whose contract gets looked up (a piped command reports its last stage), nor that enough of the real corpus comes from tools publishing a distinguishing contract to make the approach worth building — that coverage question is the solution's kill condition, and it is a count over the vault's own records rather than anything a spec can reach.
