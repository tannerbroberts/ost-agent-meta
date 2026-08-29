---
type: AssumptionTest
source: 'agent-run:unattended-sweep-2026-08-29'
created: '2026-08-29'
evidence: assertion
threshold: >-
  at least 10 of 10 type-less notes are named unread and the exit code is at
  least 1
instrument: npx vitest run test/ost/foreign-vault-blindness.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Pre-committed threshold:** at least 10 of 10 type-less notes are named unread and the exit code is at least 1. A run that reports "clean" over any of them fails, and so does one that reports the right count while staying silent about which notes went unread.

**The fixture.** A scratch vault of 10 ordinary Obsidian notes — plain Markdown, no frontmatter `type:`, the shape a person gets from writing their tree by hand. Point the checks at it.

**The assertion contract, written here because it cannot go in the command.** The instrument grammar admits exactly one form, `npx vitest run <one spec file>`; a `-t "<case name>"` filter is refused as shell punctuation, so no agent surface can name an assertion inside an existing file. The contract therefore lives in this prose and the builder is asked to make it true:

- `readTreeCensus` over the fixture reports `examined: 10` and `skipped: 10`, with each drop naming the note and the reason.
- That census is routed into a `SweepSubject` as `offered: 10, read: 0` — the pair `census.ts` already computes and `sweep.ts` already knows how to classify.
- `classifySubject` returns `totally-blind`, `sweepReport` returns `outcome: "blind"` and `exitCode: 1`, and the operator's lines contain the count and the reason rather than the word "clean".
- **The positive control, without which the green is vacuous:** the same 10 notes with `type:` frontmatter added read `offered: 10, read: 10`, classify `full`, and exit 0. That is what proves the blind verdict came from the missing frontmatter and not from a fixture that was empty, misplaced, or unreadable for some unrelated reason.

**Why this command is red today, stated honestly rather than flatteringly.** `test/ost/foreign-vault-blindness.test.ts` does not exist, so this is a `no-spec` red — it fails the way *any* question written on that path would fail, and on its own it distinguishes nothing. It is filed as a build permit only because the threshold above is a bound bar, which is what `confirmPermit` reads. What makes it worth a builder's time is not the red; it is the contract above plus the fact that both halves of the mechanism already ship and have never been connected: `TreeCensus.examined`/`skipped` on one side, `classifySubject`/`sweepReport` on the other, with `sweep.ts`'s docstring already naming "nodes in the tree" as a subject it is for.

**What a green here would NOT settle, which is most of what the parent candidate needs.** It answers feasibility and nothing else — that the grader announces its blindness instead of hiding it. It says nothing about whether the checks then produce findings a hand-builder did not already know (the sibling assumption, which needs real vault owners), nothing about whether anyone would point the tool at their vault in the first place, and nothing about whether a checker is a business. A passing spec here makes the pitch honest; it does not make it persuasive.

**Sequencing.** Cheap, mechanical, and strictly prior to the human half — there is no point asking vault owners whether the findings are useful until the checks can read their vaults at all. Settle this before spending anyone's afternoon on the sibling.
