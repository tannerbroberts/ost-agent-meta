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
