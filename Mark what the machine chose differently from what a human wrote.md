---
type: Solution
source: 'agent-ideation:2026-07-26-tenth-pass'
created: '2026-07-26'
evidence: assertion
---
#Solution #evidence/assertion
[[Do provenance markers still get read once they are on everything]]

**The idea.** Give agent-selected excerpts a visual and textual register of their own, distinct from human-authored text — so *the agent picked this line out of that node* never renders identically to *a person wrote this down as the reason*. The trust the quote earns should be the trust the selector has earned, not the trust the original author had.

**Contrast with its siblings.** The other two change *what* is shown. This changes *who the reader thinks is speaking*, and leaves the content alone. It is the only one of the three that also covers the case where the excerpt is perfectly accurate and the *selection* is what misleads — the fragment that is true, whole, and simply not the relevant sentence.

**Why it may be weaker than it looks.** Provenance markers decay: an operator who sees the same marker on every line stops reading it, exactly as this vault's operator learned to skip the root Outcome's annotations. A marker that is always present carries no information.

**Prior art in this tree.** The `#unvalidated` tag and the believability ladder are the same move at node granularity, and their track record inside this vault is genuinely mixed — 212 of 219 nodes sit at `assertion`, which is either honest floor-labelling or a marker nobody prices any more.

⚠️ Unvalidated. Agent-ideated.

## Definition of done

[[Do provenance markers still get read once they are on everything]]

```
npx vitest run test/ost/authorship-marker.test.ts
```

Green means: the marker distinguishes something. Today `unvalidated` is stamped on every agent-created node and says nothing about who wrote the prose, so a human's node and the agent's look identical. Green requires authorship recorded per node, surviving an edit and a merge rather than resetting to whoever touched it last, and reportable as a human-written share in the rollup. Green does **not** answer the test's actual question — whether readers still read the marker once it is on everything needs people.
