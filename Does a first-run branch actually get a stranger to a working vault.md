---
type: AssumptionTest
status: unvalidated
source: 'agent-run:autonomous-loop-2026-07-25-pass6'
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/mcp/bootstrap-one-question.test.ts
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

## Issues
- 2026-07-26 The product-side gap this test named is now closed (autonomous loop, pass 7,
agent-filed — not a result and not a change to the test). This node's "why it is the
riskiest assumption here" paragraph rested on a specific fact: *"v0.11.0 makes the
first-run state reportable. It does nothing to make it discoverable."* v0.12.0
(`d3efbbd`) adds `/ost-setup` — a named entry in the slash-command menu, generated from
the same `firstRun` rules as the skill so the two cannot drift. **The test is unchanged
and its threshold is untouched**: a committed root Outcome in the participant's own words
within 30 minutes, zero questions asked, any clarifying question counting as a refutation.
What changed is only that the thing under test now exists in a form worth handing to
someone. Two things still gate it and neither is a build: the package must be published
(the plugin resolves to 0.9.0, which cannot start outside a vault), and a human must send
the one-liner to the warm participant and then say nothing for thirty minutes.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/mcp/bootstrap-one-question.test.ts — Asserts the mechanical half of the threshold — that the no-vault branch reaches an initialised vault after exactly ONE question, never two: `ost_next_work` on an empty directory must return `bootstrap: true` with a single `nextStep`, and supplying only the outcome string must yield a vault whose root Outcome carries the human's words verbatim. Missing-spec red, not assertion red: this pass holds no repo-read grant, so the file does not exist and the command fails on absence. A builder should convert it to assertion red by writing the spec against today's bootstrap path first and watching the one-question count fail. It does not settle whether a STRANGER gets there — that half is a person's reaction and stays with a human.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/mcp/bootstrap-one-question.test.ts` — No test files found, exiting with code 1
