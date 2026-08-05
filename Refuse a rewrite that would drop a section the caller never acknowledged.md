---
type: Solution
source: 'TRANSCRIPT:2026-08-05-unattended-pass'
created: '2026-08-05'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A guard can catch the unacknowledged drop without refusing honest rewrites]]
[[A guard can catch the unacknowledged drop without refusing honest rewriting]]

Borrow the shape the vault already uses for concurrent writes and point it at content instead of at time. A drift guard refuses a write when the file changed since the read; this refuses a write when the *caller's own submission* shows they did not know what was in the file.

**The change:** a rewriting call must account for every `## ` section currently stored on the node — either by including it in `prose`, or by naming it in an explicit `dropping:` argument. A section present in the file and absent from both is a refusal, and the refusal names it: *"this rewrite would remove `## History`, which you did not include or list. Include it to keep it, or name it in `dropping:` to remove it."*

**What this buys.** The loss becomes impossible to cause by accident while staying possible to cause on purpose, which is the property the flat "carry everything across" rule gives up. It also converts the failure into something the caller learns from in the moment rather than discovers later by reading the file — and for an agent caller, a refusal that names the missing thing is the one form of feedback that reliably changes the next call, since it arrives before the damage instead of after.

**What it costs, honestly.** Every rewrite gets more expensive: the caller must read the node before editing it, or eat a refusal to find out what is there. That is a real tax on the common case where the caller only wants to fix a sentence. It also cannot help a caller who acknowledges a section and then fails to reproduce it faithfully — accounting for `## History` is not the same as copying it correctly, and this guard cannot tell those apart.

**Compared with its siblings.** "Carry across every section the caller did not supply" makes the mistake unrepresentable and asks nothing of the caller, but also removes the ability to delete. This keeps deletion available and makes it deliberate, at the price of assuming the caller will read a refusal and act on it — an assumption the vault's own census of thirteen sessions rediscovering one refusal should make nobody comfortable. "Report what the write changed" gives up on prevention entirely in exchange for covering losses in tools nobody has audited.

Unvalidated — proposed by the 2026-08-05 unattended pass, from a first-party reproduction of the `## History` loss recorded on the opportunity above. For human review.

## Definition of done

"Check the guard refuses a rewrite that omits a stored section and permits one that accounts for it"

```
npx vitest run test/mcp/edit-node-unacknowledged-section-guard.test.ts
```

Green means both directions hold: a rewrite omitting a stored section from both `prose` and `dropping:` is refused with the section named, and the same rewrite carrying `dropping: ["## History"]` succeeds. Red today on both counts — the `dropping:` argument does not exist, and the omit case currently succeeds silently, which is the 2026-08-05 observation that put this branch in the tree.

What green does **not** buy, and a builder should not read it as bought: the false-positive rate on real rewrites. That is what this solution actually turns on, it needs a replay of recorded edits with someone judging which were legitimate, and it is a separate test.

Named in plain text rather than as a wikilink: the test's one backlink belongs to its parent assumption, "A guard can catch the unacknowledged drop without refusing honest rewrites".
