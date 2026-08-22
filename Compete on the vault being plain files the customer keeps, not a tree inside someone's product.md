---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Buyers have been burned by lock-in recently enough to pay for portability]]
[[Everything the tree's claims rest on is readable without the tool, not just the claims themselves]]

The differentiator is the artefact, not the reasoning. What this produces is a folder of Markdown with wikilinks and a git history — readable in Obsidian, greppable, diffable, reviewable in a pull request, and entirely intact if the tool disappears tomorrow. A funded competitor's tree lives in their database and leaves as an export, if it leaves at all.

This is a claim about switching costs and continuity, aimed at a buyer who has been through one tool sunsetting already.

**Compared to the alternatives.** The most concrete of the three and the easiest to demonstrate in thirty seconds, because it is a property of the output rather than a claim about quality. It is also the narrowest: it wins only against hosted competitors, says nothing about whether the discovery is any good, and a funded team could ship a file-based export and blunt most of it. Positioning on refusals makes a stronger claim that is much harder to prove; the head-to-head diff would prove something but takes weeks.

**What would make this the wrong pick.** Most buyers do not price portability until they need it, and by then they are not shopping. This may be a real advantage that nobody pays for — which is a different failure from not having an advantage, and needs a different test.

## History
- 2026-08-05 unlinked "Ask ten buyers what happened the last time a tool they relied on shut down" — moved under "Buyers have been burned by lock-in recently enough to pay for portability" — the belief this test measures now has a node of its own

## Definition of done

"Count how many cited sources a reader can open with the tool gone and the dot-directories hidden"

```
npx vitest run test/product/vault-portability.test.ts
```

Bar: at least 95 of every 100 `source:` pointers on live nodes resolve to a file outside any dot-directory. Below that, the "entirely intact if the tool disappears tomorrow" line is narrowed in the copy rather than repeated.

**This is the feasibility half only.** Green proves the artefact has the property being sold. It says nothing about whether a buyer pays for portability — that is the assumption "Buyers have been burned by lock-in recently enough to pay for portability", and a person is the measurement for it. Do not read a green here as the position being validated.

The command is a `no-spec` red today: the file does not exist, so it fails for the reason any unwritten spec fails. The bar above is what makes it a build permit anyway, and the assertion — not the filename — is the work.
