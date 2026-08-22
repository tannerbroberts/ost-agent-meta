---
type: AssumptionTest
source: 'agent-ideated:2026-08-22-unattended-sweep'
created: '2026-08-22'
evidence: assertion
threshold: >-
  At least 95 of every 100 source pointers on live nodes resolve to a file
  outside any dot-directory; below 95 the portability copy must name the limit
  before it ships
instrument: npx vitest run test/product/vault-portability.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**Pre-committed threshold:** at least 95 of every 100 `source:` pointers on live nodes resolve to a file a reader can open with the tool removed and dot-directories hidden. Below 95, the claim "entirely intact if the tool disappears" is narrowed in the copy rather than repeated.

**What the spec does.** Walk a vault's live nodes, take each node's `source:`, resolve it to the record it names, and classify the resolved path as reader-visible or dot-hidden. Report the share, then assert the bar. Two controls carry it, because without them the assertion passes against a resolver that answers for everything: a node whose source names no stored record must count as unresolved rather than silently skipped, and a fixture with its evidence relocated out of `.ost-agent/` must move the share, or the test is measuring the walk and not the layout.

**Why it is red today.** `test/product/vault-portability.test.ts` does not exist, so this is a `no-spec` red and it is declared as one rather than dressed up: it fails for the same reason any unwritten spec fails. The bar above is what makes it a working permit anyway — `confirmPermit` keeps a no-spec permit when the threshold is bound — and the builder's definition of done is the assertion, not the filename. The mechanism it would be red *about* is named and checkable without running anything: this vault's evidence records sit under `.ost-agent/evidence/`, and Obsidian excludes dot-directories from the vault view.

**What this does NOT settle.** Nothing about desirability. A green here proves the record is portable; it says nothing about whether any buyer prices portability, which is the sibling assumption "Buyers have been burned by lock-in recently enough to pay for portability" and is correctly a person's. It also says nothing about the other three verbs in the pitch — greppable, diffable and reviewable in a pull request are all true of dot-directories and are not in question here.

⚠️ Unvalidated. Agent-designed; nobody has run it.
