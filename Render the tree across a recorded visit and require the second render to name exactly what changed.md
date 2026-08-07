---
type: AssumptionTest
created: '2026-08-07'
evidence: assertion
threshold: >-
  Against a fixture vault: render, record the visit, then make three changes of
  different kinds — a new node, a status transition, and a merged duplicate —
  and re-render. The second render must name all three and nothing else. Zero
  false positives is the bar, because a diff that flags unchanged nodes is one a
  reader stops reading.
instrument: npx vitest run test/cli/tree-view-diff-since-last-visit.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**What this measures.** Whether a per-visit diff is derivable from the vault alone: a fixture vault is rendered, the visit is recorded, three semantically different changes are made — a node created, a status set, a duplicate merged away — and the vault is rendered again. The second render must name those three nodes and no others.

The three change kinds are chosen because they fail differently. A created node is the easy case and any file-mtime scan finds it. A status transition changes frontmatter only, so a renderer reading bodies alone misses it. A merge deletes one file and rewrites another, which a naive diff reports as one deletion plus one unrelated edit rather than as one event — that is the case that decides whether the diff is computed from the vault's own semantics or from the filesystem.

**Why it is red today.** This vault's records describe no per-visit diff and no rendered view command; the solution beneath which this sits is `status: unvalidated` and has never been reported as built. So both the spec file and the mechanism it asserts are absent, and the command fails. **Stated plainly because it weakens the test:** with no repository sight on this surface I could not confirm that no such spec already exists, so this instrument's red is the weaker kind — an absent file — rather than assertions going red against a module that exists and behaves differently. A builder picking this up should expect to write the mechanism, not to fix one.

**What a green here would NOT settle.** Everything the solution is actually for. It would not show that a reader orients faster, that the view is legible at this tree's real size — 1071 nodes — or that structure is what a stakeholder wants rather than an answer to "are we on track?". Those belong to "A rendered tree orients a reader faster than the files do", which is a reader-measured claim and stays with people. A green exit code here must not be read as evidence that anyone was oriented.

⚠️ Unvalidated, agent-proposed. Nobody has run it.

## Instrument Log
- 2026-08-07 **red** (exit 1) `npx vitest run test/cli/tree-view-diff-since-last-visit.test.ts` — No test files found, exiting with code 1
