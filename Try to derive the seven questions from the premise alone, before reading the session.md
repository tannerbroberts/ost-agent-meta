---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  At least 4 of the 7 actual questions are derived, with at most 3 invented
  ones.
instrument: npx vitest run test/loop/premise-consequence-set.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that consequences can be derived in advance. Several of the seven only became visible after work was done — the duplicated refusal template, the severed ingestion — and against genuinely emergent questions this offers nothing.

**Risk category: feasibility.**

**Design.** Give someone only the premise — "only serve Claude subscription users" — plus the state of the project at that moment, and ask them to list every decision that follows. Then compare against the seven actually asked. Count hits, misses, and invented questions that never arose.

**Why it is small.** One premise, one derivation, and the answer key already exists in the transcript.

**What it will not cover.** A derivation attempted with hindsight about the domain, even by someone who has not read the session, is easier than one attempted cold at the time. The miss count is the reliable half of the finding.

A human runs this and records the result.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/loop/premise-consequence-set.test.ts — Asserts the consequence set is derived from the stated premise before the run begins, presented as one batch with each item's dependency and proposed default, and that the run then proceeds without stopping unless it meets something outside the covered set. Red today because nothing derives consequences up front — a run discovers each question when it hits it.

## Instrument Log
- 2026-08-07 **red** (exit 1) `npx vitest run test/loop/premise-consequence-set.test.ts` — No test files found, exiting with code 1
