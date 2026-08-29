---
type: Solution
source: 'INBOX:2026-08-11-observed-build-loop-reports-not-merged-on-merged-prs.md'
created: '2026-08-11'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[The founder will actually maintain a highlight criteria note over time]]

A small durable note in the vault — "what counts as a highlight" — that the founder edits in his own words and every reporting surface consults before deciding what to push. Seeded with the two classes he already named (a red test going green; a long-standing branch dying, with reasons), and grown by him as surfaced non-highlights teach him what he did not mean.

**Against the alternatives beside it:** this attacks the blocker the founder actually stated — "I haven't found a good way to helping you determine what's worth sharing" — by making the sharing criteria a durable, editable artifact instead of a judgement re-guessed every firing. It is the only candidate that improves the other two rather than competing with them (both flip announcements and digests would read it). Its own risk is viability: a criteria note only works if the founder actually maintains it, and every prior artifact that asked for recurring founder input is evidence to check that belief against.

## Issues
- 2026-08-29 2026-08-29 unattended sweep, repo sight held: examined for a missing instrument and deliberately left without one. Recording the examination because this node carried no prior note and would otherwise be re-read from scratch by every firing that meets it in `solutionsMissingInstruments`. The only belief beneath it, "The founder will actually maintain a highlight criteria note over time", is viability about one person's behaviour over months, and its test — "Seed a one-line criteria note and see whether the founder edits it within two weeks" — has a two-week wall-clock and a human editor as its measurement. No exit code encodes whether someone kept a note current. Note one cheaper route a human may prefer: the same question is partly answerable from history rather than by waiting, since the sibling candidate "An operator-set evidence window in ost.config.yaml, amended by hand like discovery.target" already proposes reading amendment counts out of the vault's git log for exactly this class of belief — if the founder has never amended a comparable hand-held artefact, that is evidence about this belief obtained for the price of reading a log. What a human should do: set the lane with `ost-agent lane --set`, since `ost_flag_humans_required` is withheld on the unattended surface. Not a skipped step.
