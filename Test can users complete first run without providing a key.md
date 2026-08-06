---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-22-agent-as-driver.md'
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/cli/first-run-without-key.test.ts
---
#AssumptionTest #ported-from-ost-agent-vault #evidence/assertion

**Risk category: Usability.** Riskiest assumption: making the key optional (off by default) doesn't confuse setup — users reach a first successful run without thinking they need a key.

**Proposed test (small, fast):** Moderated setup test with ~5 new users; observe whether they complete a first pass without supplying a credential and whether the optional-key path is understood.

**Pre-committed success threshold:** 5 of 5 complete a first run without a key; none blocked or confused about whether a key is required.

_Proposal only — a human runs this with real users. Unvalidated._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-06 instrument: (none) → npx vitest run test/cli/first-run-without-key.test.ts — Drives a whole first run with no credential in the environment — no ANTHROPIC_API_KEY, no ant CLI, no keychain entry — and asserts every step of the default path completes rather than refusing: init, set-outcome, ingest, and the maintenance passes. It is red today for an observed reason, not a missing file: this vault's own friction record of 2026-07-25 ("run P2-P5 requires an API credential even when an authenticated ambient agent is the one driving") records the Anthropic SDK failing to resolve an authentication method with an authenticated session right there, and the run only proceeded via the ambient tool-surface workaround. So the keyless path is known to be incomplete at P2-P5, and this spec fails on exactly that. It settles the mechanical half of the assumption only — whether any part of the first run demands a key. Whether a stranger would experience that path as complete is usability and stays with a person.

## Issues
- 2026-08-06 Lane finding, unlabelled because the label was refused. This test is humans-required: its method is a "Moderated setup test with ~5 new users", its threshold is "5 of 5 complete a first run without a key; none blocked or confused", and confusion is a state of a person. The closing line says "a human runs this with real users". This pass attempted `ost_flag_humans_required` and was denied the tool, so the frontmatter carries no `lane:`. A human should set it with `ost-agent lane`.

Worth separating before anyone runs it, because the test currently conflates two claims. That a first run *completes* with no key is mechanical and may already be true — the skill states this project calls no model at all and needs no API key — so a spec asserting only completion would pass today and measure nothing. The half that is genuinely open is the second clause: whether a new user believes a key is required. That is the usability claim, it is the reason the test needs people, and it is the one the threshold should be written around. Splitting the mechanical half into its own instrumented test would leave a smaller, sharper human study.
