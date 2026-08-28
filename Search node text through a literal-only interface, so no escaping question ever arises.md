---
type: Solution
status: unvalidated
source: 'TRANSCRIPT:8a9777ad-a1ca-47fc-ab8e-3bd4b001a5cd'
created: '2026-08-06'
evidence: observed
authorship: machine
---
#Solution #unvalidated #evidence/observed
[[Nearly every search a pass issues is a literal lookup wearing a pattern language]]

Remove the pattern language from the path where node text is searched, rather than learning to quote for it.

Every recorded failure of this kind has the same origin: a sentence a person wrote — a node title containing a brace, an asterisk, a quote — was handed to something that reads punctuation as instruction. `{Charge` and `*{threshold` were never patterns. They were the first characters of two titles in this vault.

The proposal is a search entry point that takes text as data and nothing else. No glob, no regex, no shell word-splitting: a caller asks "which nodes contain this exact string" and the question cannot be malformed, because there is no syntax to malform. Where a pass genuinely needs pattern matching it reaches for a different, explicitly-named call, and that call's arguments are written by hand rather than interpolated from tree content.

The bet is that the overwhelming majority of searches a pass actually issues are literal lookups wearing a pattern language's clothes. If that is true, this candidate eliminates the entire class rather than mitigating it, and it does so at the boundary rather than at every call site — which is the difference between a fix and a discipline.

If it is false — if passes routinely need real pattern semantics over node text — then a literal-only interface just moves the calls to the escape hatch and the failures come back through it. That is the assumption worth settling before building, and it is settled by counting, not by arguing: the searches a pass issues are recorded.

Against its siblings. "Never let a malformed search be counted as an empty result" is strictly more robust and strictly less satisfying — it tolerates the failure and prevents the miscount, and it keeps working for denied reads and size caps that no escaping fixes. "Route every data-derived argument through a quoter" keeps the pattern language and adds a rule that must be remembered, which is the shape of fix this project has elsewhere concluded is not enough on its own. This candidate is the only one of the three that makes the mistake unavailable rather than survivable, and it is also the only one whose scope claim might be wrong.

## Definition of done

"Census the recorded searches and split them by whether their argument came from the tree"

```
npx vitest run test/telemetry/search-literality-census.test.ts
```

Run this before building. It is as likely to redraw the solution as to confirm it — if tree-derived arguments turn out to be overwhelmingly literal while hand-written ones are freely patterned, the interface should be drawn on provenance, not on literalness, and this node wants rewriting rather than implementing.

Green here bounds only searches over node text. The shell failures in the same opportunity — a path globbed, a flag read as a filename — are untouched by it.

## The census has been built and run — corrected 2026-08-28, unattended sweep with repo sight

This section replaces a claim that had gone false. The definition of done above used to carry the line: *"Red today: the trace records search invocations but nothing classifies them by pattern-need or by argument provenance, so the census has nothing to read."* That was true when written and is not true now, and a reader arriving at this node was being told the gating measurement did not exist when in fact it exists, has run, and passed.

**What was verified first-party this pass.** `ost_read_repo` probed `test/telemetry/search-literality-census.test.ts`: it is present at 21,854 bytes. The test node beneath this solution — "Census the recorded searches and split them by whether their argument came from the tree" — carries that exact command as its `instrument` field, and its own instrument log records two runs on 2026-08-06: a **red** (exit 1, "No test files found") followed by a **green** (exit 0, 2.67s). So the spec was written and went from red to green on the day it was commissioned. Nothing was executed by this pass; the green is read off the recorded exit code, not re-observed.

**The distinction that matters, and it is the reason this is not simply good news.** A green instrument here says the census *computes* — that the classifier exists and the four cells can be filled. It does not say what the census *found*. The test's pre-committed bar is "at least 90% of tree-derived search arguments in the recorded trace are expressible as literal lookups", and no verdict against that bar is recorded on the test node. So the measurement this solution said should be run before building has been built and executed, and its answer has never been read out. The decision the census was commissioned to make — literal-only interface, or an interface drawn on provenance instead, or this candidate losing to its siblings — is still open, and is now open for a worse reason than before: not because the evidence is missing, but because it was collected and not reported.

**What a human owes this node**, in one command, and it is cheap because the counting is already done:

```
ost-agent result "Census the recorded searches and split them by whether their argument came from the tree" -v <supported|refuted|inconclusive> -n "<the four cell counts, and the tree-derived literal percentage>" -b <you> -u "<what this run left uncovered>"
```

The test's own prose already names what a verdict must not overclaim: the trace records searches that were *issued*, not searches that were wanted, which biases the census toward this solution's preferred answer.

**Nothing else about this node changed.** The proposal, the sibling comparison, the scope caveat and the definition-of-done command are reproduced unaltered; only the stale redness claim was removed and this section added in its place.

_Method, first-party to this firing (2026-08-28): `ost_read_repo` probe of `test/telemetry/search-literality-census.test.ts`, and `ost_read_tree` on the test node including its recorded instrument log. No command was run, no result recorded, and no rung moved._

## History
- 2026-08-28 body edited — The definition of done asserted "Red today: the trace records search invocations but nothing classifies them by pattern-need or by argument provenance, so the census has nothing to read." Verified false this pass: test/telemetry/search-literality-census.test.ts exists at 21,854 bytes (ost_read_repo probe), and the test node beneath this solution records a red then a green run of exactly that command on 2026-08-06. A reader was being told the gating measurement did not exist when it exists and passed. Removed the stale sentence and added a section stating what the green does and does not settle — the census computes, but its verdict against the pre-committed 90% bar was never recorded — with the ost-agent result command that would close it. Every other claim in the body is reproduced unaltered.
