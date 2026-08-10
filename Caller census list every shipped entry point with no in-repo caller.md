---
type: Solution
source: >-
  INBOX:friction/2026-08-10-friction-pr-80-shipped-a-pass-claims-the-work-item-before.md
created: '2026-08-10'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A static walk can tell an unreached entry point from a reached one well enough to be read]]

**The idea.** A report, not a gate. Walk the repository's exported surface — CLI subcommands registered in `src/cli/`, MCP tools registered in `src/mcp/`, exported functions in `src/` — and for each one count callers that are not its own spec file. Print the ones whose only reader is their test. The count is the artefact; nobody is blocked by it.

**Why a census first.** This tree already knows what happens when a guard is built before its subject is measured: `src/ost/sweep.ts` says so about itself in its own doc comment — the guard it ships fires on total blindness only, would have stayed silent on the very failure that produced it, and the module's second half exists solely to *record* the partial case so an operator can decide later whether the guard earns its keep. That is the pattern to copy here. One instance (`claim.ts`) is not a rate, and a rate is what decides whether this is worth a gate.

**Contrast with siblings.** "Refuse to call a solution shipped until something reaches it" is the gate this census would justify or kill — it cannot be judged before the number exists. "A shipped CLI command must appear in an automation script" is narrower and stricter: it fixes one class by fiat, cheaply, and would not have needed this census to be right about `claim`.

**Where it fails.** A caller count is a bad proxy in both directions. Dynamic dispatch, string-keyed command tables and shell invocations from `examples/` are all callers a static walk will miss, so the report will accuse live code; and a function called only from other dead code counts as reached, so it will miss the deepest instances. It is a starting denominator, not a verdict, and shipping it as though it were one recreates this node's parent problem inside the fix.

**Cost.** Small — one module, one CLI subcommand, no schema change and no new state.

⚠️ Unvalidated. Agent-ideated.

## Definition of done

"Run the census and check it accuses claim without accusing the eight commands build-pass invokes"

```
npx vitest run test/product/caller-census.test.ts
```

Quoted rather than linked: the test hangs under the Assumption "A static walk can tell an unreached entry point from a reached one well enough to be read", and a title is wikilinked exactly once in the vault.

Red today as **`no-spec`** — the file does not exist, which is the weakest reason a command can fail. The assertion that gives it meaning is written out on the test node: the census must name `claim` and must not name the six subcommands `build-pass.sh` reaches through `node "$CLI" <subcommand>`.
