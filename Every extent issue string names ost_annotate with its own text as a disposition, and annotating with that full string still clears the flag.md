---
type: AssumptionTest
source: 'agent-ideation:2026-08-21-unattended-sweep'
created: '2026-08-21'
evidence: assertion
threshold: >-
  3 of 3 rules (shared-extent, subset-extent, entangled-extent) emit an issue
  string containing "ost_annotate", and for each of the 3 a fixture vault
  annotated with that full string reports 0 extent issues and done: true on the
  next computeNextWork.
instrument: npx vitest run test/ost/extent-issue-names-clear.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** In-memory fixtures plus a temp vault, the shape `test/ost/extent.test.ts` already uses; no credential, no person.

**What the spec asserts.** For each of the three verdicts in `EXTENT_RULES`, build the minimal forest that produces it (the three fixtures in `test/ost/extent.test.ts` — same extent, strict subset, crossing overlap at 0.5), take the issue string `scanExtentOverlap` yields, and `expect(issue).toContain("ost_annotate")`. Then, in a temp vault initialised with `initVault`, reproduce the shared-extent case, run the real `ost_annotate` tool with `{ title, issue }` using the new longer string, and assert `computeNextWork(...).hygieneIssues` has no extent rule and `done` is true — proving the longer text did not break the whole-string match.

**Why it is red today, and for a reason specific to this question.** The strings emitted by `src/ost/extent.ts` today end at "rewrite each from its own evidence and say what separates them" and contain no tool name; the first assertion fails on the mechanism, not on a missing import. An empty spec would go green, so this is not a no-spec red by construction — but **this surface cannot write the spec file, so until someone does, the command fails on `No test files found` and is filed `no-spec`, granting no permit.** The builder's job is the file, with the assertions above.

**What a green does NOT settle.** That any future pass reads the instruction and quotes it. Usability is observed over firings, not asserted in a spec, and the parent assumption says so.

⚠️ Proposed only — the agent does not run tests or record results.
