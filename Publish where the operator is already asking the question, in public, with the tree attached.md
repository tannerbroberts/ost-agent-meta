---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[Publishing real discovery work brings strangers who try it]]
[[The vault has a publishable form that carries its provenance without carrying the raw evidence bodies]]

Take the discovery work already being done and do it in public — the vault, the trees, the assumption tests and what they came back with, including the ones that killed an idea. Post it where people who care about product discovery already gather. The artefact is the marketing, and it costs nothing extra because the work is happening anyway.

What makes this plausible rather than generic content marketing is that the output is unusually legible. A tree with provenance, an evidence ladder, and a public history of what was refused is a demonstration that cannot be faked by a screenshot.

**Compared to the alternatives.** Cheapest of any distribution route, compounds slowly, and it reaches exactly the people who would value the thing that makes this tool different. It is also the slowest, entirely dependent on one person's continued output, and it reaches an audience of practitioners who are more likely to copy the method than to buy the tool.

**What would make this the wrong pick.** Publishing a real vault means publishing real evidence, and a vault about the author's own product is one thing while a customer's vault is quite another. This route works for exactly as long as the author is the only customer.

## History
- 2026-08-05 unlinked "Publish six pieces over six weeks and count strangers who arrive and try it" — moved under "Publishing real discovery work brings strangers who try it" — the belief this test measures now has a node of its own

## Definition of done — the mechanical floor, added 2026-08-29

This candidate carried exactly one assumption, and it was the human one ("Publishing real discovery work brings strangers who try it"). Its mechanical premise sat unstated: the pitch turns on publishing something that still carries provenance — "a demonstration that cannot be faked by a screenshot" — and nothing establishes that such a form exists or is safe to post. The prose's own last line gets close, naming that "publishing a real vault means publishing real evidence", but treats it as a limit on *whose* vault rather than as a question about whether a publishable form exists at all.

That belief is now on the tree as "The vault has a publishable form that carries its provenance without carrying the raw evidence bodies", with one test beneath it:

"A published vault carries every source id and none of the evidence bodies"

```
npx vitest run test/security/publishable-vault-export.test.ts
```

Bar: zero of 3 seeded private strings survive into the published form, and at least 1 source id still resolves to its actor and rung. Both clauses matter — publishing nothing passes the first and fails the second, which is the cheap way to fake a redaction test. The command is a `no-spec` red, so the assertion contract a builder should satisfy lives in the test node's body rather than in the command.

**The repository fact that makes this worth a builder's time.** `test/security/` holds 27 specs and every one guards what may *enter* the product — credentials, tainted arguments, tool allowlists, data framing, gate coverage. No spec anywhere asserts an outbound-disclosure property, and no export, publish or redact module exists in `src/`. This is not thin coverage of a built mechanism; it is a mechanism nobody has built. (Bound: `src/cli/index.ts` is 158KB and was probed, not read, so an inline publish command is not ruled out.)

**What this does not touch.** The distribution objections above stand unchanged — slowest route, dependent on one person's output, reaches practitioners more likely to copy the method than buy the tool. No spec speaks to those. Nothing here was executed and no result is recorded.
