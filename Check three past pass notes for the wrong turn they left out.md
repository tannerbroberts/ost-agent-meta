---
type: AssumptionTest
source: 'agent-ideated:2026-08-02-maintenance-pass-2'
created: '2026-08-02'
evidence: assertion
instrument: npx vitest run test/adapters/session-retrospective.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: desirability, with a hard honesty component.** Whether an agent's own account of a session names the wrong turns that session actually took.

**The assumption under test.** That self-report is truthful enough to be evidence. The candidate concedes the bias in its own body; this test measures it instead of arguing about it, and it can be run today because **this vault has been accumulating agent self-reports for weeks.** The `## Pass note` sections on [[OST-Agent (meta)]] are exactly the artifact the candidate proposes to institutionalize — written by the agent, at the end of its own session, about how the session went.

**The test — existing artifacts, nothing to build, nothing to run forward.** Pick three pass notes whose sessions also left a transcript and a commit range. For each, a human reads the independent record first and lists the wrong turns visible in it, then reads the pass note and scores two things:

- **Omission.** Wrong turns the record shows and the note does not mention.
- **Addition.** Wrong turns the note names that the record could not have revealed — the misconceptions only the agent had access to, which is the entire value proposition of self-report.

**Pre-committed threshold.** **≥1 addition per session on average, and zero sessions omitting the largest wrong turn the human finds in the record.** The second half is the kill condition and it is deliberately unforgiving: a retrospective that is candid about small slips and silent about the expensive one is worse than no retrospective, because it reads as coverage. On failure the candidate closes in favour of [[A model reads the raw transcript and files what the pattern scan cannot see]], which has no session to defend.

**Relationship to [[Diff three past sessions' claims against their traces by hand]].** That test asks whether the agent's *counts* match the record; this one asks whether its *account of its own confusion* matches. Same method, same corpus, different failure mode — a note can be arithmetically perfect and still omit the day it spent going the wrong way. A human may reasonably choose to run them as one sitting, and should; they are filed separately because they close different candidates.

**Who runs it.** A human, reading the record before the note so the note cannot frame the reading. No results recorded here.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/adapters/session-retrospective.test.ts — Asserts the design question the node says this candidate has to survive — that it can stay silent credibly: a session with nothing conceptual to report produces no inbox item rather than a "nothing notable" one, while a retrospective that is written lands with the session id as provenance and enters at the assertion floor as self-report. Red today because nothing is required before a session closes and no retrospective path exists.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/adapters/session-retrospective.test.ts` — No test files found, exiting with code 1
