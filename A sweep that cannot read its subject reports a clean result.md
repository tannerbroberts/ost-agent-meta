---
type: Opportunity
created: '2026-07-27'
evidence: assertion
---
#Opportunity #evidence/assertion
[[Every count states the denominator it was taken over]]
[[A check with an empty subject is a failure, not a pass]]
[[Seed every sweep with a known-present instance it must find]]

**The need (operator's voice):** "The sweep told me 5 and 12. The real answer was 6 and 15. It never said it had failed to open four of the files it was counting — it just counted the ones it could open and printed a total that looked finished."

**What was observed, 2026-07-27 (eleventh pass).** A compute-only history sweep run against both vaults skipped every node whose filename contains an em-dash. Git quotes non-ASCII paths in `--name-only`, `git show <sha>:<path>` failed on the quoted form, and the sweep's error branch was `continue`. Four affected files were never read. The output carried no denominator and no error, so the number looked like a measurement of the whole population when it was a measurement of the readable subset.

**Why this is not the same need as [[A failed pass reports success, so my automation can't tell]].** That one is about a run that ERRORED and exited 0 — there is a failure, and it is hidden. This one is about a run in which nothing failed: every file the sweep opened, it classified correctly, and it reported exactly what it found. The defect is in what it never reached. A supervisor watching exit codes catches the first and cannot catch the second, because there is no error to catch.

**Why it matters more than the specific bug.** The whole product is a machine that reports on a tree nobody is watching. A count with no denominator is indistinguishable from a complete count, and the operator's only signal is the number itself. This tree has now met the shape three times — a test that could not fail, a lane reader that reported a fragment as a declaration, and now a sweep that measured the subset it could open — which suggests it is a habit of the codebase rather than three accidents.

**Litmus (more than one way?):** yes — reporting unreadables alongside findings, failing on a zero subject count, printing a coverage denominator, and asserting the sweep can see a known-present instance are genuinely different answers.

⚠️ Agent-filed from an observed failure in this pass's own instrument.

## History
- 2026-08-01 evidence: observed → assertion — demoted by the fifteenth pass — B3's rung-unearned guard (v0.23.0-line) shipped after this node was authored; its source is not a TRANSCRIPT: recording, so 'observed' was unearned. Demotion only, per rungs.ts's own remedy.
