---
type: AssumptionTest
created: '2026-08-06'
evidence: assertion
threshold: >-
  Every shipped solution resolves to real code in the product repo AND carries a
  History line stating the evidence for the promotion; one failure refutes.
instrument: npx vitest run test/ost/shipped-status-audit.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Assumption under test (feasibility, with a safety edge).** That `status: shipped` in this vault currently means built, so excluding those solutions hides nothing that still needs chasing.

**The test.** For every solution marked `shipped`, resolve the modules and specs its own `## History` or body names — `src/ost/node.ts` and rule `wrapped-wikilink`, the Vault write guard, the `uncovered` field — and assert each is present in the product repository. Assert also that every `shipped` status carries a History line stating the evidence for it, since an unexplained promotion is the shape the dodge would take.

**Pre-commit before running:** all currently-shipped solutions must resolve to real code, and all must carry a reasoned History line. A single one that does not refutes the assumption and the exclusion rule must not ship without a gate in front of the status field.

**What this does NOT settle.** Whether the shipped code does what its node claims — resolving a module proves it exists, not that it is correct. And nothing here bears on whether the exclusion makes the queue more useful to a human, which is desirability and needs a person reading a shorter queue.

**Lane: compute-only.**

⚠️ Proposed only — the agent does not run tests or record results.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/ost/shipped-status-audit.test.ts` — No test files found, exiting with code 1

## Partial audit already done — 2026-08-09 (not a result, and not a lane change)

**No result is recorded and no lane is claimed.** This test is filed as needing a person because, when it was written, no surface here could open the product repository. That premise changed: `ost_read_repo` is granted to the unattended discovery pass as of the 2026-08-09 config commit, and this pass used it. What follows is what that bought, so whoever runs this test does not start from zero — and so the lane question gets asked on current facts rather than stale ones.

**Three of the five shipped nodes in `solutionsMissingInstruments` were audited against committed code:**

| Node | What was read | Verdict |
|---|---|---|
| Refuse a write whose content is empty or literally undefined | `test/ost/vault-write-guard.test.ts`, in full | Claim confirmed in detail — eight bad values refused, every content-bearing write path covered, and a positive control asserting the guard cannot pass vacuously |
| Refuse a wiki-link that contains a newline | same file, in full | Claim confirmed in detail — refused at all six free-text parameters, refusal names the flattened title, three must-stay-writable cases pinned |
| Refuse a proving command whose exit code cannot report failure | `test/loop/` directory listing only | Presence only — `exit-laundering.test.ts` exists; the file was not opened, so what it asserts is unverified |

The other two — "A result must state what it did not cover" and "Post-session transcript harvester" — were not audited this pass.

**What this suggests about the lane, stated as a question rather than a change.** The audit's expensive half turned out to be mechanical: read the spec file named by the claim, check its assertions against the claim's words. That is a command's work, and a spec asserting *"every node carrying `status: shipped` names a spec file that exists in the repository"* would be a real instrument, red today. What is *not* mechanical is the judgement this test's threshold actually asks for — whether a spec's assertions are the same claim the node makes, which is reading, not matching. So the honest shape may be a split: an instrument for the presence half, a person for the correspondence half.

This pass did not relabel anything. `ost_flag_humans_required` is withheld from the unattended surface, `ost_set_instrument` would have contradicted the lane already declared here, and re-cutting a test into two is a change of question rather than a change of form. Both are a human's call, and the second is the one worth making.

**Method and its limits:** two spec files listed, one read in full, findings recorded on each subject node. Agent self-observation of this product — it grounds feasibility, not demand. Nothing was executed; a spec that exists is not a spec that passes.
