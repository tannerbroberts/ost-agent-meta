---
type: AssumptionTest
source: 'agent-run:unattended-sweep-2026-08-27'
created: '2026-08-27'
evidence: assertion
threshold: >-
  exactly 1 sighting from the unwrapped-MCP-refusal fixture and 0 from the
  non-zero-exit fixture
instrument: npx vitest run test/loop/corrections-envelope.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility. Small and fast: two fixtures and one function call.**

Drive `extractRefusals` (`src/loop/corrections.ts`) over two hand-built transcript fixtures and assert opposite verdicts:

- A `tool_result` with `is_error: true`, **no** `<tool_use_error>` wrapper, carrying the real refusal this tree has paid for three times — `"is not an instrument form. The allowed forms are: vitest-spec (npx vitest run <path>.test.ts)"` — attributed to a `mcp__ost-agent__ost_set_instrument` `tool_use` block. Must yield **one** sighting, whose `permitted` names the vitest form and whose `tool` is the MCP tool.
- A `tool_result` with `is_error: true` carrying a plain non-zero-exit failure whose text includes a remedy cue but names no permitted form. Must yield **zero** sightings.

A third case is worth pinning in the same file because it is the regression the deleted line was guarding: the `String to replace not found in file.` shape, with a long quoted payload containing "must", must still yield zero.

**Why it is red today.** `extractRefusals` currently discards the first fixture before `splitRefusal` sees it, because `GUARD_MARKER` requires the `<tool_use_error>` wrapper that an MCP server never emits. The first assertion therefore fails against today's code, and goes green exactly when the candidate above is built.

**Honest labelling of how red it is.** `test/loop/corrections-envelope.test.ts` does not exist yet, so the first run of this command will be filed `no-spec` rather than a true red — it would fail identically for any question written on that path. That is a real weakness and it is not concealed here. Two things reduce it, both grounded in this tree's own recorded evidence rather than asserted: the file names a directory that **does** exist and is populated (`test/loop/` already holds `corrections-ledger.test.ts`, so a builder lands beside the conventions and fixtures for this exact module), and the threshold above is a bound numeric bar, which is the property this vault's 2026-08-09 finding identified as what actually carried a builder through a missing spec in the one weak-red lifecycle it has watched end green.

**It is written this way because the stronger form is not expressible on this surface, not as a shortcut.** The instrument grammar in `src/knowledge/instruments.ts` accepts exactly `npx vitest run <path>.test.ts`; a `-t` filter naming one assertion inside the existing `corrections-ledger.test.ts` is rejected twice over, as shell punctuation and as an unknown form. So the choice available was a bare new path or nothing. This is already recorded on "My instruments are red because a file is absent, not because the behaviour is", measured at the tool boundary on 2026-08-21, and this test is another instance of it rather than a new finding.

**What a green here does not settle.** That the ledger stays readable in practice — this is two fixtures, not the 588 harvested sessions sitting in this vault, and the noise question can only be answered by replaying those. It settles the mechanism, not the consequence. And it says nothing at all about desirability: no evidence here bears on whether carrying these corrections forward changes what any later session writes.
