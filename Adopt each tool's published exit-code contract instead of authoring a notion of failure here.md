---
type: Solution
source: 'agent-ideation:2026-09-02-unattended-sweep'
created: '2026-09-02'
evidence: assertion
killIf: >-
  A count over this vault's own friction records shows fewer than half the
  errored Bash events came from tools that publish a distinguishing exit-code
  contract.
killBy: '2026-12-01'
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[The numeric exit code reaches the harvester at all, rather than being formatted away for a human reader]]

**Variation dimension: bought-vs-built — how much of the judgement is imported. Position taken: the whole discrimination is adopted from outside, and what is built here is only the lookup.**

The distinction this opportunity wants already exists, published, in the tools themselves, and has for decades. `grep` documents exit 0 for a match, 1 for no match, and 2 or above for an actual error. `diff` documents 0 same, 1 differs, 2 trouble. `vitest` exits 1 when tests failed and reserves other codes for crashes. Every one of these already separates *the answer was no* from *I broke*, in a contract their maintainers keep. Authoring a heuristic here re-derives, worse, something that is already specified.

So: read the numeric exit code, look up the invoked tool's published contract in a small imported table, and file `tool_error` only for the codes that tool documents as trouble. `no match` becomes an ordinary negative answer because grep's own manual says code 1 means that, not because this repository decided it looks like one.

**Why this position and not another.** Both siblings invent a rule that this repository then owns and must keep true as tools change. This one owns nothing but a mapping and can cite a source for every row in it, which also makes it the only one of the three whose correctness a reviewer can check against a document rather than against the author's judgement.

**Cheapest form.** A constant in `src/adapters/transcript.ts` — tool name to the set of exit codes that tool publishes as *findings* rather than failures — consulted in the `is_error` arm once the exit code is in hand. Start with the handful this vault's own records actually contain (`grep`/`rg`, `vitest`, `diff`, `gh`) and let anything unlisted keep today's behaviour, so the change is strictly a demotion of cases somebody can point at a manual for.

**The dependency that makes or breaks it, stated plainly.** It needs the exit code as a number, and the adapter does not have one. `resultText()` flattens the result content to a string and the code survives only as the prose `Exit code 1` at the head of the body; `FrictionEvent` has no field for it. So this candidate's first unit of work is extracting a number out of text the host formats for humans — and if the host ever stops printing that line, the whole approach loses its input. The assumption beneath this node is aimed there rather than at the table.

**What it deliberately does not do.** It cannot reach anything the tool does not publish. A bespoke script, a `node -e`, or any command whose exit codes are the author's private business falls straight through to today's behaviour — correctly, because nothing outside was bought for that case. The kill condition above is a direct measurement of how large that hole is.

**How this differs from "Take the host's own error flag as the definition of friction instead of authoring one here", which sits under a neighbouring opportunity.** That candidate adopts the *host's* `is_error` flag and treats it as authoritative. Here the host's flag is precisely the thing that is wrong — it is set on every non-zero exit and is the mechanism that produced this need. What is adopted here is the *tools'* contracts, one layer below the host, and adopting them means overruling the host flag rather than deferring to it. The two nodes take opposite positions on the same question of whose judgement to import.

**What it gives up, plainly.** Like the caller-declaration sibling it is prospective for anything whose exit code was never printed, and the table is a maintained artifact after all — a small one with citations, but somebody still owns it.

**Honest note on how this was ideated.** All three candidates under this opportunity were composed in one context by one author. This unattended surface holds no grant to run independent parallel ideators, so the blindness the ruleset asks for was not available and their apparent distinctness should be discounted accordingly.

Unvalidated. Agent-ideated 2026-09-02; a human to review.

## Definition of done

"A friction event from a Bash result carries the exit code as a number and names the tool that returned it"

```
npx vitest run test/adapters/friction-exit-code.test.ts
```

The bar that command has to clear: 5 of 5 well-formed bodies yield the correct number, 2 of 2 malformed yield `null`, and zero bodies yield a wrong number. The `null` requirement is load-bearing — a parser that guesses hands the adopted lookup table a confident wrong row.

The test title is quoted rather than wikilinked on purpose: its one backlink belongs to its parent assumption.

**And the half no command reaches.** This is the first unit of work, not the whole candidate: the lookup table itself is untested by it, and so is the coverage question — how much of the real corpus comes from tools that publish a distinguishing contract — which is this candidate's kill condition and a count over the vault's own records.
