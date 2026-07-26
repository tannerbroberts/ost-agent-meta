---
type: AssumptionTest
status: unvalidated
source: 'agent-run:autonomous-loop-2026-07-25-pass6'
created: '2026-07-25'
evidence: assertion
---
#AssumptionTest #unvalidated #usability #evidence/assertion

**Assumption under test (usability).** That a person handed only the one-line pitch —
install the plugin, the session sets it up — reaches a committed Outcome node without
anyone from inside the building typing anything or answering a question.

**Why it is the riskiest assumption here.** v0.11.0 makes the first-run state
*reportable*. It does nothing to make it *discoverable*. A stranger who installs a
plugin and opens a session sees no prompt, no banner, and no reason to believe
anything is waiting for them; the bootstrap branch only fires once they ask for
discovery work, which is the thing they installed the tool in order to learn how to
do. Every other assumption under this opportunity is downstream of whether that first
minute happens at all.

**Proposed test.** The warm n=1 participant the founder has already lined up. Send the
one-liner and nothing else — no walkthrough, no link to the README, no availability to
answer questions for the first thirty minutes. Watch what lands in their vault's git
log.

**Pre-committed threshold:** the participant reaches a committed root Outcome node
carrying their own words within 30 minutes, with zero questions asked of the founder.
Any question asked, or any founder-supplied instruction beyond the one-liner, is a
**failure** of this assumption and must be recorded as one — the claim under test is
precisely that the one-liner suffices. A participant who gets there in 25 minutes
after one clarifying question has refuted this, not narrowly passed it.

**What it does NOT test.** Whether they run a second pass, whether the tree they
produce is any good, or whether anyone who is not already interested would install it
at all. It tests one minute of one warm participant.

**n=1, and the vault must not launder it.** A single participant cannot clear
[[Cold-offer test - will outside teams hand over real discovery work]]'s 5-of-20
threshold and must not be recorded against it. What it can produce is this vault's
**first external-operator evidence of any kind**, at the `observed` rung, which is
more than 208 nodes of founder and agent sourcing have managed.

**Lane: deliberately unset.** It needs a real outside person; classifying it is a
human's call.

⚠️ Proposed only — the agent does not run tests or record results.
