---
type: Solution
source: 'TRANSCRIPT:2026-08-05-unattended-pass'
created: '2026-08-05'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A rewrite can preserve every unsupplied section without the caller naming any of them]]
[[A rewrite can preserve every unsupplied section without the caller naming one]]

Today a rewriting tool protects a **list** of section headings. `ost_edit_node` names three — `## Results`, `## Uncovered`, `## Instrument Log` — reattaches those verbatim, and lets everything else in the old body go. The failure this opportunity records happens in the gap between that list and reality: `## History` is governed by a rule saying it is append-only and correctable only by appending, and it is not on the list, so it is silently dropped.

**The change:** stop enumerating what to keep, and derive it. Treat any `## ` section present in the stored node but absent from the caller's `prose` as *not addressed by this call*, and carry it across unchanged. The caller's prose replaces the sections it actually contains; everything else survives by default.

**What this buys.** The protection stops depending on somebody having remembered to add a heading to a list. A section invented next quarter is protected the day it is invented, and the class of bug where the rules say a section is inviolable while the mechanism has never heard of it becomes unrepresentable.

**What it costs, honestly.** It inverts the default, and defaults have victims. Deleting a section becomes impossible through this tool — omission now means keep, so there is no gesture that means remove. That is arguably correct for this vault, where removal is meant to be a human's call on the CLI, but it should be chosen rather than backed into. It also carries stale prose forward silently: a caller who rewrites a node's argument and expects an obsolete section to fall away will find it still attached, which is a quieter wrong than the one it fixes but still a wrong.

**Compared with its siblings.** This one prevents the loss by construction and needs nothing of the caller — the weakest assumption about who is paying attention, which matters when the caller is an unattended agent. "Refuse a rewrite that would drop a section the caller never acknowledged" catches the same class at the boundary instead and teaches the caller what it nearly did, at the price of a chattier call. "Report what the write changed, so a silent loss stops being silent" prevents nothing at all but covers losses nobody anticipated, including in tools this fix never touches. They are not alternatives so much as three different bets about where the leverage is: in the mechanism, in the contract, or in the feedback.

Unvalidated — proposed by the 2026-08-05 unattended pass, from a first-party reproduction of the `## History` loss recorded on the opportunity above. For human review.

## Definition of done

"Edit a node holding five sections while supplying two, and check the other three survive intact"

```
npx vitest run test/mcp/edit-node-preserves-unsupplied-sections.test.ts
```

Green means: a node's unsupplied sections — including `## History`, including one already on the hand-listed reserved set, including one whose body holds a fenced block containing a `## ` line — survive a rewrite byte-identical, with nothing duplicated. Red today, and for the right reason rather than because a file is absent: the `## History` loss this asserts against was observed first-party on 2026-08-05.

Named in plain text rather than as a wikilink deliberately. The test's one backlink belongs to its parent assumption, "A rewrite can preserve every unsupplied section without the caller naming any of them"; a second link from here would fail the `single-backlink` invariant. This pass confirmed that mechanic the hard way — an `ost_edit_node` call that reproduced a node's child links in `prose` produced a duplicate of each, because the tool reattaches the link header itself.
