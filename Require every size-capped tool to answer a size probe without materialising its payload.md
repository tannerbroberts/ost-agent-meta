---
type: AssumptionTest
source: 'TRANSCRIPT:28d14def-76a2-4bbb-bd55-6f9b80c8ca8c'
created: '2026-08-06'
evidence: assertion
threshold: >-
  Every tool that can be refused for response size answers a size probe, and for
  each one the probe's work is strictly less than producing the response —
  asserted by the probe not invoking the serialiser. A tool that can only size
  itself by building the payload fails, and failing is the informative outcome.
instrument: npx vitest run test/mcp/size-probe-precedes-refusal.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** This is a property of the tool implementations, settled by a spec that spies on the serialiser. It is not about anyone's preferences.

**What it does.** Enumerate every tool with a response-size cap. For each, call the size probe with the serialiser stubbed to throw. A tool whose probe completes has a genuinely cheap size; a tool whose probe explodes was building the payload to measure it. Assert the first for all of them, and expect `ost_read_tree` to be the one that argues.

**Why it is red today.** No size probe exists on any tool, so every case fails at the first call. This is missing-mechanism red rather than merely missing-file red — the caps themselves are real and observed, and the absent thing is the probe. The path is still named from vault convention rather than read off the suite, because this pass had no repository sight; a human should confirm the location.

**What a green does NOT settle.** That a caller who is told a size in advance actually behaves differently. Sizing is necessary for the solution and nowhere near sufficient for it, and a green here must not be read as evidence that the friction went away.
