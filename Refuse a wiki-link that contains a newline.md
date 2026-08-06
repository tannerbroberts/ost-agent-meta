---
type: Solution
status: shipped
source: 'agent-run:autonomous-loop-2026-07-26-pass7'
created: '2026-07-26'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A newline inside a wiki-link catches breaks that nothing else catches]]

**The idea.** `ost-agent check` fails on any `[[…]]` whose contents contain a newline.
One rule, mechanical, no judgement, no false positives — a wiki-link with a line break in
it is never intentional and never renders as an edge.

**Why this, and why now.** Four occurrences across the two live vaults, all the same
shape, none of them caught by anything:

| When | Where | Cause |
|---|---|---|
| 2026-07-25 (pass 4) | `tetrix-ost` root Outcome | prose wrapping |
| 2026-07-25 (pass 6) | `tetrix-ost` — *Let the invited stranger play the board they were sent* | prose wrapping |
| 2026-07-25 (pass 6) | `ost-agent-meta` | prose wrapping |
| 2026-07-25 (pass 6) | `ost-agent-meta` "A first-run branch that walks a stranger to a vault in one question" — two links | prose wrapping |
| 2026-07-26 (pass 7) | `tetrix-ost` — twice, in the same pass, in its own new writing | prose wrapping |
| 2026-07-26 (pass 7) | `ost-agent-meta` — **inside the briefing paragraph declaring this a defect** | prose wrapping |

The last entry is the one that settles it. An agent that has flagged this failure three
times, in a pass whose explicit brief included flagging it, broke a link inside the
sentence announcing the fix —
because a hard-wrapped paragraph and a node title long enough to cross a column boundary
are both things this system encourages. **Discipline has now been tried and has failed six
times, by the party that keeps writing the flag.** The remaining options are a check or
acceptance. Every one of the six was repaired only because a throwaway scan was run by
hand before committing; nothing in the product would have caught any of them.

**Why it belongs under this opportunity.** The operator's complaint here is *"eight nodes
quietly stopped existing as far as the agent is concerned, and nothing warned me."* A
wrapped link is the same event with a different cause: an edge that a human wrote, that
reads correctly in the source, and that does not exist in the graph. Obsidian renders it
as plain text with brackets, which is easy to miss in a wall of prose, and the graph view —
the artifact this whole product produces — simply lacks the line.

**How it compares to its siblings.**
- "Detect renames from link topology and repair the edge" infers intent and repairs.
  This asserts a syntactic fact and refuses. It is strictly cheaper and strictly dumber,
  and it catches a case rename detection cannot see, because the target never existed
  under any name.
- A general dangling-link check (already partly present, and where the `wikilinks`
  false positive lives) has to decide whether an unresolved target is a typo, a
  not-yet-created node, or prose inside backticks. This one does not: a newline inside
  the brackets is unambiguous.

**Where this fails, stated so it can be judged rather than assumed.** It catches the
*wrapped* case and nothing else. A link mistyped on a single line, or pointing at a node
that was never created, sails past it. It is a narrow rule that happens to cover 4 of the
4 real occurrences observed — which is an argument from a small sample, and the sample is
this loop's own writing habits, not any external operator's.

**Cost.** A regex in the existing invariant pass and one test. Smaller than the annotation
that reported the fourth occurrence.

⚠️ Unvalidated. Proposed by the agent that caused two of the four occurrences, which is a
reason to trust the observation and discount the conviction.


## Shipped — v0.13.0, and the assumption test ran first — 2026-07-26

`ost-agent` `1790775` on `main`, tagged `v0.13.0` locally. `check` now fails with rule
`wrapped-wikilink`; `ost_next_work` and the `P5_hygiene` pass report it beside dangling
links and orphans; a ruleset rule tells the agent the writing habit so the party that
causes this defect is instructed and not only caught. 360 tests across 53 files (up from
351), `tsc` clean, `npm pack` clean.

**Two things came out different from what this node predicted.**

*The cost estimate was right and the placement was wrong.* This node said "a regex in the
existing invariant pass and one test." The regex is four lines. But the same link scan
already existed in three places — `checkInvariants`, `computeNextWork`'s hygiene detector,
and `P5_hygiene`'s — so shipping it in one of them would have meant the check and the
hygiene pass disagreeing about what a defect is. `wrappedLinkTargets` went into
`src/ost/node.ts`, beside the grammar it is the inverse of, and all three call it. Worth
recording because the pattern is likely to repeat: this product's structural rules are
duplicated across a checker and a reporter, and any new one has to be added to both.

*The detective half was the easy half.* The rule catches the defect at commit time; it does
nothing about the writing habit that produces it, and the habit belongs to an agent that
reads the ruleset. So the ruleset gained the rule too, and it renders into `SKILL.md`.
Whether telling the agent works is untested and probably untestable in one pass — the next
few passes' own writing is the sample.

**What it does not do, restated so it is not over-claimed.** It catches the wrapped case
only. A link mistyped on one line, or pointing at a node nobody created, still sails past
it — the dangling-link rule catches the second and nothing catches the first.

## History
- 2026-08-01 evidence: observed → assertion — demoted by the fifteenth pass — B3's rung-unearned guard (v0.23.0-line) shipped after this node was authored; its source is not a TRANSCRIPT: recording, so 'observed' was unearned. Demotion only, per rungs.ts's own remedy.
- 2026-08-05 unlinked "Does refusing a newline inside a wiki-link catch breaks nothing else catches" — moved under "A newline inside a wiki-link catches breaks that nothing else catches" — the belief this test measures now has a node of its own
- 2026-08-05 status: unvalidated → shipped — The node's own body records this as shipped in ost-agent v0.13.0, commit 1790775 on main: `check` fails with rule `wrapped-wikilink`, `ost_next_work` and `P5_hygiene` report it, and `wrappedLinkTargets` lives in src/ost/node.ts with all three callers using it. Recorded as `shipped` by the 2026-08-05 unattended sweep because it was sitting in `solutionsMissingInstruments`, and a red-now instrument is impossible for behaviour that already ships — a spec asserting the rule would pass on arrival, so it could not fail and would measure nothing. Status corrected instead of an instrument invented. This says the mechanism is built; it does not say anyone has judged it worth having, which is still what its assumption test is for.

## Issues
- 2026-08-06 Probably already shipped — do not write an instrument for this without checking first, because it would be green on the day it was written and would therefore measure nothing.

The ruleset this vault's agents operate under states the guard as existing behaviour: a wrapped wikilink "produces bracketed text and no edge", and "`check` fails on it (rule wrapped-wikilink) and the hygiene pass reports it, because discipline alone has repeatedly not been enough." That is the product's own documentation describing the refusal in this node's title as present tense.

This pass could not confirm it against the code. `product.repos` is unconfigured, so `ost_read_repo` is unavailable, and reads of the product directory were denied — both recorded separately as their own opportunities. So this is an inference from documentation, not a verification.

For a human: if the guard is in fact shipped, this solution wants its status changed and its test recorded as answered, and neither is an unattended surface's call. If it is not shipped, the ruleset is describing a guard that does not exist, which is a sharper problem than the missing feature and belongs under "A guard derived the rule it was checking, so it agreed with the bug for 23 releases".

Two siblings from the same era carry the same suspicion and were not checked either: "Refuse a proving command whose exit code cannot report failure" — `ost_set_instrument` already rejects shell punctuation and non-spec commands, which is at least part of that claim — and "Refuse a write whose content is empty or literally undefined". Both should be checked against the repository before anyone writes an instrument for them.
