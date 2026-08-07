---
type: AssumptionTest
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
threshold: >-
  Against a fixture tree of the current scale — 62 solutions missing
  instruments, 337 tests — every test named in the response carries an
  `instrument` field or an explicit null, and all four capped lists still return
  25 entries each.
instrument: npx vitest run test/ost/next-work-instrument-visibility.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**What it measures.** Whether the field is affordable at the size this tree actually is. The fixture is deliberately built at current scale rather than at a convenient one, because the whole risk is that the response is already being cut and this makes the cut deeper.

The explicit-null half matters: a field that is present only when set cannot be distinguished by a reader from a field that is absent because the report ran out of room, which reintroduces the ambiguity the candidate exists to remove.

**Why it is red today.** The sweep reports which solutions lack an instrument and never reports the instruments themselves, so there is no field to assert on.

**Honest limit on the instrument.** This pass had no repository sight — `ost_read_repo` is unconfigured and direct reads of the product checkout were denied — so the named spec file does not exist and its first red is a missing path rather than a failing assertion against `computeNextWork`. The weak form of red, recorded rather than hidden; see "My instruments are red because a file is absent, not because the behaviour is".

**What a green here does not settle.** Whether a pass handed the field reads it. That is the candidate's stated failure mode and it is about behaviour under budget pressure, not about the response shape.
