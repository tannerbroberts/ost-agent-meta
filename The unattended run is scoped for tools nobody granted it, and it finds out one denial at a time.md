---
type: Opportunity
status: unvalidated
source: 'TRANSCRIPT:8a9777ad-a1ca-47fc-ab8e-3bd4b001a5cd'
created: '2026-08-06'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed
[[Preflight the run's tool demands against its grant and stop at turn one]]
[[The run's report leads with what it was refused, so a denied night cannot read as a quiet one]]
[[Derive the permission allowlist from the skill's own allowed-tools, so the two lists cannot drift]]

I set a run going while I am asleep, and it spends the night being told no.

Five unattended firings recorded the same thing. Session `8a9777ad` asked for `ost_flag_humans_required` four times in a row and was denied four times, then asked for `ost_check` and was denied. Session `6e66c934` asked for the same tool four times and was denied four times. Sessions `21d0f730`, `7449e571` and `1a8f25fb` each hit it too — `ost_check` in all three, plus `ost_debt` and `ost_status`. Across those five sessions the message is identical every time: "Claude requested permissions to use X, but you haven't granted it yet." Reading the product's own source hit the same wall: `Glob` was refused on `/Users/tanner/dev/OST-Agent` in four separate runs, and `ost_read_repo` failed differently but for the same reason — "no product repos configured".

The instructions the run is given name these tools. The grant it is handed does not include them. Nothing compares the two before the run starts, so the mismatch surfaces as a denial in the middle of work, after the run has already decided what it was going to do and against a person who is not there to say yes.

Two things are wrong with this and only one of them is the missing permission. The other is that a denial to an unattended run is indistinguishable, from where I sit the next morning, from work that simply was not needed. The run reports what it did; it does not report the shape of what it was stopped from doing. So a night of denials reads as a quiet night.

What I want is to know before I walk away that the run can do the job I set it, and to be told plainly if it could not.

## Provenance

Cited record: `TRANSCRIPT:8a9777ad-a1ca-47fc-ab8e-3bd4b001a5cd`. The same pattern is independently recorded in `6e66c934-24d8-4200-b6f2-7af23002c478`, `21d0f730-05c0-4cf8-8cd2-ecdea5444bba`, `7449e571-40b5-47b6-a1cd-3b2c1c85322e`, and `1a8f25fb-1259-4b80-8b53-32fbfde38e54`. All five are marked in the transcript as "this vault's own unattended firings — nobody was watching". Frontmatter carries one id because citations are matched exactly; the others are named here in plain text.

This is the agent's own usage captured mechanically. It grounds usability, not desirability.

## Observed again during the pass that created this node

This node was distilled from five transcript records, and then the same thing happened to the pass writing it. Two denials, first-party rather than reconstructed:

- `ost_debt` — "Claude requested permissions to use mcp__ost-agent__ost_debt, but you haven't granted it yet." Called to find which assumption tests sat beneath which solutions, which is the one question that bucket of work needs answered.
- `ost_flag_humans_required` — same message. Called to label three tests whose own prose names outside people as the measurement.

That makes six independent sessions, and this one is the strongest evidence of the set: the other five are recollections assembled by an adapter from transcripts, while this one was observed as it happened by the agent that then had to work around it.

Both denials had a workaround and neither was free. The `ost_debt` question was answered instead by reading `ost_read_tree`, overflowing its output cap, and grepping the vault's files directly — four calls and a spilled tool result to replace one. The `ost_flag_humans_required` calls could not be worked around at all: three tests that should carry a `lane:` marker still do not, and the finding was written into their `## Issues` sections as prose, where nothing that reads the field will see it. A reader checking lanes mechanically still sees three unlabelled tests that look runnable.

That second case is the sharper form of this opportunity than the one the body above describes. A denied read costs turns. A denied *write* leaves the tree carrying a claim in a place no gate reads, and the pass that recorded it looks, from its own summary, like it handled the item.

Provenance: this pass, 2026-08-06. Not an ingested record — no adapter has captured this session yet, and citing an id for a session that has not ended is the exact fault flagged on four nodes elsewhere in this vault this morning.
