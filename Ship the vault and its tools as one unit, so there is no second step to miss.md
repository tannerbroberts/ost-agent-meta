---
type: Solution
status: unvalidated
created: '2026-08-02'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A vault opened from an unrelated directory can yield its own tools]]

Change the packaging rather than the configuration: make the vault itself carry what is needed to operate on it, so that opening the vault anywhere yields the tools, with no separate enabling artifact in a directory that may or may not be the one the session opened.

**Compared with the alternatives:** this is the only candidate that survives the vault being moved, copied, or opened from an unexpected working directory — the class of problem the observed failure actually belongs to, since the plugin was declared correctly and simply never launched. It is also the most invasive, it constrains how the product can be distributed, and it may not be achievable within the host's plugin model at all. That last point is the feasibility question worth settling before anyone builds it.

Unvalidated, agent-ideated: a candidate for comparison, not a recommendation.

## Definition of done

"Try to load the tools from inside the vault directory at all"

```
npx vitest run test/mcp/vault-declared-tool-load.test.ts
```

Green means a vault carrying its own tool-server declaration yields the `ost_*` surface when it is opened from an unrelated working directory. It is red today because nothing in the repository reads a tool declaration out of a vault.

**This is the disconfirmer that should run before any of this candidate's siblings.** The whole idea rests on the host's plugin model loading a server declared from inside the vault rather than from the project directory the session happened to open, and that may simply not be possible. It is also the most invasive of the three to build, so a negative answer here is cheap and removes the most expensive option from the consideration set — which is the best outcome a test of this shape can have.

**Why it is a spec rather than an afternoon.** The node's threshold reads as a stopwatch — "demonstrated once, within one afternoon" — but what it actually asks is whether a resolution path exists, and a fixture vault plus a working directory set somewhere unrelated answers that without anyone's afternoon. The afternoon was a proxy for cheapness, not the measurement.

**What green does NOT settle.** It shows the tools resolve, not that shipping them this way is right. The packaging cost, the upgrade story for a vault that carries its own copy of the server, and whether an operator wants their vault to be executable at all are all untouched — and the last of those is the substance of "Would an operator accept the agent living inside the vault it maintains".

## History
- 2026-08-05 unlinked "Try to load the tools from inside the vault directory at all" — moved under "A vault opened from an unrelated directory can yield its own tools" — the belief this test measures now has a node of its own
