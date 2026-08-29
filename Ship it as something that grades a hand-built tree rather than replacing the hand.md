---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[Checks over a hand-built vault surface findings its owner did not already know]]
[[Pointed at a vault it did not author, the checks report they could not read it rather than reporting it clean]]

Concede the generation. Someone who enjoys doing discovery by hand should keep doing it by hand — that is the part they are good at and the part they want. Point the tool at the vault they already have and let it run the checks: what ladders up to nothing, which solutions rest on no tested assumption, which claims sit above the rung their sources earned, which wikilinks are broken.

The question stops being "why would I use this instead" and becomes "why would I not run this over what I already have", which is a much easier question to win.

**Compared to the alternatives.** The lowest-friction of the three by a wide margin — no migration, no workflow change, nothing to abandon — and it reaches people who would never adopt a replacement. It also gives up most of the value proposition and most of the price: a checker is worth less than a discovery partner, and this frames the product as the smaller thing permanently.

**What would make this the wrong pick.** It may be a strictly worse business built on a strictly easier sale. It is also the one option that does not answer the opportunity as written — it makes the question go away rather than answering it, and if the real want is a reason to believe the tool is better, this supplies none.

## History
- 2026-08-05 unlinked "Run the checks over three hand-built vaults and count findings the owner did not already know" — moved under "Checks over a hand-built vault surface findings its owner did not already know" — the belief this test measures now has a node of its own

## Definition of done — the mechanical floor, added 2026-08-29

This candidate carried exactly one assumption, and it was the human one ("Checks over a hand-built vault surface findings its owner did not already know"). Its *mechanical* premise sat unstated in the prose above: "point the tool at the vault they already have and let it run the checks" presupposes that the checks can read a vault this tool did not author. Read off the code this pass, that presupposition is in real doubt — a note with no frontmatter `type:` lands in `skipped`, `readTree()` returns an empty node list, and zero violations over zero nodes is reported as a pass. So the pitch as written would hand a stranger a clean bill of health on a vault nothing read.

That belief is now on the tree as "Pointed at a vault it did not author, the checks report they could not read it rather than reporting it clean", with one test beneath it:

"A vault of notes carrying no type frontmatter reads as totally blind, not as a clean check"

```
npx vitest run test/ost/foreign-vault-blindness.test.ts
```

Bar: at least 10 of 10 type-less notes are named unread and the exit code is at least 1. The command is a `no-spec` red — that file does not exist yet — so the assertion contract a builder should satisfy is written into the test node's body rather than into the command, because the instrument grammar accepts one spec path and no case filter.

**Sequence this before the human half.** There is no point asking hand-builders whether the findings are useful until the checks can read their vaults; a refuted verdict here retires the pitch for the price of one spec, and a supported one is the precondition the sibling assumption needs.

**What this does not touch.** The commercial objections in the prose above stand unchanged — that this concedes most of the value and prices the product as the smaller thing permanently. Those are positioning calls and no spec speaks to them. Nothing here was executed and no result is recorded.
