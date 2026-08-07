---
type: AssumptionTest
created: '2026-08-07'
evidence: assertion
threshold: >-
  Enumerate every write on the agent tool surface and attempt, through each, to
  record the root Outcome as achieved while no external signal is declared. All
  must refuse. One path that succeeds fails the test — a gate with one way
  around it is not a gate.
instrument: npx vitest run test/ost/outcome-signal-gate.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**What this measures.** Whether the no-self-certification rule is held by construction or by convention. The spec enumerates the agent surface's write tools rather than naming a list by hand — that enumeration is the point, because the failure mode this guards against is a path nobody remembered to close — and drives each one at the root Outcome with no external signal declared. Every path must refuse.

The interesting cases are not `ost_set_status`, which already lacks `validated`. They are the prose paths: whether `ost_append_to_node` and `ost_edit_node` can write "outcome achieved" onto the root in ordinary text, and whether a declared signal can itself be declared by compute. If a signal the agent can write is a gate the agent can open, the guarantee is decorative, and this test is how that gets found before anyone relies on it.

**Why it is red today.** The tree holds no record of an outcome-signal declaration existing, and the prose paths demonstrably accept arbitrary text — this pass used both. So the mechanism is absent and the spec file with it. **The weakening caveat, stated because it matters to whoever picks this up:** this surface has no repository sight (`product.repos` unconfigured, direct reads denied), so I could not verify that no such spec exists. The red is most likely an absent file rather than assertions failing against a real module.

**What a green here would NOT settle.** Whether any team can name an external signal worth gating on, whether the signal they choose measures what they believe it measures, or whether the human CLI escape hatch gets used routinely. All three are how this solution fails in the field, none has an exit code, and all stay with "Teams can define an external signal that decides whether their outcome was met" — the reader-and-buyer-shaped belief beside this one.

⚠️ Unvalidated, agent-proposed. Nobody has run it.

## Instrument Log
- 2026-08-07 **red** (exit 1) `npx vitest run test/ost/outcome-signal-gate.test.ts` — No test files found, exiting with code 1
