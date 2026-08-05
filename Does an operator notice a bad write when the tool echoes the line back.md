---
type: AssumptionTest
source: 'agent-ideation:2026-07-26-tenth-pass'
created: '2026-07-26'
evidence: assertion
instrument: npx vitest run test/mcp/echo-written-line.test.ts
---
#AssumptionTest #evidence/assertion

**The single assumption.** That echoing the written line is *read* — by a human at a terminal, and by an unattended agent parsing tool output. The solution's whole value is early detection, and early detection by an audience that skims is no detection.

**The evidence against it is already on file, and it is this pass.** This pass called `ost_annotate` twice, received `annotated "<title>"` twice, and moved on. It found the defect minutes later by grepping for something else entirely. An echo would have put `undefined` on screen — and there is no honest reason to think this pass would have stopped on it, because it did not stop on the two identical `- 2026-07-26 undefined` lines it had already read in full while looking at that very node.

**Proposed test.** Give operators a session transcript containing ~20 tool calls, one of which echoes a destroyed write, and ask them to summarise what the session accomplished. Do not mention errors. Count who flags it unprompted.

**Lane: humans-required.** It measures whether people notice something, which is not derivable from inside.

**Pre-committed threshold.** The echo earns its place if **at least 3 of 5** operators flag the bad line unprompted. **One or zero refutes it** — the echo is decoration, and the defence has to be a refusal rather than a report. Two is inconclusive and the test gets re-run with a longer transcript, because 20 calls may be short enough to read exhaustively in a way real sessions are not.

**A cheaper prior question that should be settled first, and costs nobody.** Does any unattended caller in this codebase actually *inspect* mutating tool output, or is it discarded? If it is discarded everywhere, the agent half of the audience is answered without recruiting anyone, and only the human half needs the test above.

⚠️ Proposed only — the agent does not run tests or record results.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/mcp/echo-written-line.test.ts — Asserts every mutating tool returns the line it actually wrote rather than a confirmation that it wrote something. Red against today's code, observed directly this pass: ost_set_instrument already echoes its full History line, but ost_annotate returns `annotated "<title>"`, ost_append_to_node returns `appended to "<title>"`, and ost_create_node and ost_link_nodes report only that the call completed — so the defect this node was ideated from is still expressible on four surfaces.
