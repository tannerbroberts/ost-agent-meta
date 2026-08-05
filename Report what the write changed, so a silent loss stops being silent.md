---
type: Solution
source: 'TRANSCRIPT:2026-08-05-unattended-pass'
created: '2026-08-05'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Being told a section was dropped is worth little to a caller who cannot restore it]]

The two siblings both try to stop the loss. This one accepts that some losses will not be anticipated and attacks the property that made this one expensive: **nothing in the response distinguished a write that preserved everything from a write that destroyed a record.** `ost_edit_node` returned `edited the body of "…"` in both cases.

**The change:** every mutating tool returns what it did to the node's structure — sections replaced, sections kept, sections added, and sections **dropped**, each by heading. Not a diff of prose; a census of parts. The dropped list is the one that matters and should be present even when empty, so its absence is never mistaken for none.

**What this buys.** It is the only one of the three that covers losses nobody predicted, in tools nobody audited, including ones written later. It is also the cheapest to build and the cheapest to be wrong about: it changes no behaviour, refuses nothing, and cannot break a caller that ignores it. And it is the only one that would have caught this particular bug *without anyone first knowing the bug existed* — the 2026-08-05 pass discovered the `## History` loss only because it happened to have read the whole file minutes earlier for an unrelated reason.

**What it costs, honestly.** It prevents nothing. The record is still gone; the caller is merely told. That is worth much less when the caller cannot act on it — an unattended pass that reads `dropped: ["## History"]` has no undo, and its only remedy is to reconstruct the content from whatever it still holds in context, which on this occasion worked by luck and usually will not. There is a real risk this ships, makes everyone feel covered, and leaves the destruction rate unchanged.

**Compared with its siblings.** Think of it as insurance rather than a fix, and it should probably be built *alongside* whichever of the other two is chosen rather than instead of one. "Carry across every section the caller did not supply" and "Refuse a rewrite that would drop a section the caller never acknowledged" each close the specific hole and each depend on somebody having correctly enumerated what matters; this one assumes that enumeration will eventually be wrong and makes the wrongness visible. If a human is choosing one, this is the weakest. If a human is choosing an order, this is plausibly the first, because it is the one that tells you whether the others worked.

Unvalidated — proposed by the 2026-08-05 unattended pass, from a first-party reproduction of the `## History` loss recorded on the opportunity above. For human review.

## Definition of done

"Check every section reported dropped arrives with enough to restore it"

```
npx vitest run test/mcp/mutation-response-dropped-sections-recoverable.test.ts
```

Green means every heading in a mutating response's `dropped` list arrives with either the section's prior text or a git ref to read it at, and that a lossless write still carries an empty `dropped` key — so absent is distinguishable from none. Red today because no such report exists in any form: the tool returns the same success string whether it preserved everything or destroyed a `## History`.

Two cautions for whoever builds this. Green proves a caller *could* restore, not that one would — and this solution's own assumption is stated against it, arguing that reporting may convert a silent loss into a documented one without changing the loss rate. Build it alongside one of the two preventive siblings rather than instead of one.

Named in plain text rather than as a wikilink: the test's one backlink belongs to its parent assumption, "Being told a section was dropped is worth little to a caller who cannot restore it".
