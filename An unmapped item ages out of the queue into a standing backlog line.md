---
type: Solution
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[Ageing an item out does not bury a novel one]]

**The idea.** An evidence item that has been offered to N passes and mapped by none stops being listed individually. It joins a single line — "62 items aged out, oldest 2026-07-24" — that is always visible and never expands unless asked for.

**Why this shape.** It is the only candidate here that makes no claim whatsoever about what the items mean. Nothing is discarded, nothing is asserted to be a duplicate, nothing is filed against a node. The queue simply stops presenting as fresh work something that eleven consecutive passes have declined to act on, which is information the sweep already has and currently ignores.

Worth stating plainly: this is the floor, not the answer. It is here because the two siblings both require judgement the surface may not be trusted with, and a tree needs a candidate that survives the decision that judgement is too expensive.

**How it compares to its siblings.**
- "An evidence item can be filed as corroboration of a node that already exists" is the ambitious one — it puts frequency on the tree. This one puts frequency nowhere; it just stops repeating the question.
- "The queue groups identical friction shapes into one item with a count" compresses by similarity and can be wrong about similarity. This compresses by age and cannot be wrong, because age is not a judgement.

**Where it fails, stated so it can be judged.** Ageing is a proxy for *irrelevant* and it is a bad one here. The items in this backlog were not skipped because they were uninteresting; they were skipped because the surface had no way to discharge them, which is a tooling gap. Ageing them out converts a visible tooling gap into an invisible one, and the count that made the gap arguable — "it has only ever grown" — stops being confrontational the moment it is one line.

The failure mode is therefore that this ships, the complaint goes quiet, and neither sibling ever gets built.

**Cost.** Lowest of the three. A counter per item and a summary line.

⚠️ Unvalidated. Agent-ideated.

## Definition of done

"A novel item survives the age-out that buries its neighbours"

```
npx vitest run test/evidence/age-out-preserves-novel.test.ts
```

Written without repo sight, so its first red is an absent file. Note that passing requires consulting something besides age — which, if it holds, means this candidate is less judgement-free than its body claims.

## 2026-08-29 — this is built, and the vault has simply not turned it on

**Read with repo sight, which the pass that wrote this node did not have.** `test/evidence/age-out-preserves-novel.test.ts` exists in the product's suite and holds two named tests. The first seeds twenty-one equally-old records — twenty repeating an already-mapped signature, one novel — and asserts that the twenty collapse into `agedOutEvidence: { count: 20, oldest: OLD }` while the novel one stays individually listed and every file stays on disk. The second asserts that **with no `evidence.ageOutDays` configured, nothing ages out no matter how old**.

**So the knob is `evidence.ageOutDays`, and this vault has not set it.** That is why `ost_next_work` returned `agedOutEvidence: { count: 0, oldest: null }` on 2026-08-29 while listing 457 unmapped items, 432 of them not even shown. The second test above is a precise description of the state this vault is in.

**Three corrections to this node's own text, stated rather than edited in.**
1. The `## Definition of done` block says the instrument was "written without repo sight, so its first red is an absent file." The file is no longer absent. Whether `npx vitest run test/evidence/age-out-preserves-novel.test.ts` is red or green today is not something this pass can know — it does not run tests — and it needs `ost-agent verify` to settle. But the weak `no-spec` red that block warns about is no longer the reason it would fail.
2. The body's central claim — that ageing "makes no claim whatsoever about what the items mean" and "cannot be wrong, because age is not a judgement" — is contradicted by the spec that was built for it. The implemented rule is **age AND redundancy with an already-mapped signature**, and the spec's own header says so: "AGE ALONE MAY NEVER COLLAPSE AN ITEM." The body already anticipated this in its closing line; the spec has now settled it. This candidate is not judgement-free, and the reader should not compare it to its siblings as though it were.
3. The body's stated failure mode — "this ships, the complaint goes quiet, and neither sibling ever gets built" — is worth re-reading against what actually happened. It did not ship *and* go quiet; it shipped and was never enabled, so the complaint has been loud (457 items) for a different reason than the one predicted.

**What a human could do in one line, and what it would and would not buy.** Setting `evidence.ageOutDays` in `ost.config.yaml` would collapse the redundant tail of the friction queue — the near-identical `tool_error`/`retry` session records that ten consecutive sweeps have declined to map — while, per the first spec test, leaving anything novel individually listed. What it would *not* do is discharge the underlying gap: those records were never skipped because they were uninteresting, they were skipped because an Opportunity carries one `source` id and the surface has no verb for "this record corroborates a node that already exists." That gap belongs to the sibling "An evidence item can be filed as corroboration of a node that already exists," and enabling age-out would make it less visible, exactly as this node's own **Where it fails** paragraph predicts.

**Not acted on by this pass.** `ost.config.yaml` is the operator's file and no tool on this surface writes it. Recorded here rather than on the Outcome because it is a fact about this candidate, not a ledger of the sweep.
