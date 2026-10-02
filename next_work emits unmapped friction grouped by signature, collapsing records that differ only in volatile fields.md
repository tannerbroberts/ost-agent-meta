---
type: AssumptionTest
source: 'agent-ideation:2026-10-01-unattended-sweep'
created: '2026-10-02'
evidence: assertion
threshold: >-
  at least 2 seeded records differing only in path and session id fall into
  exactly 1 group, and 0 records with different tool names share a group
instrument: npx vitest run test/mcp/next-work-signature-groups.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.**

A small, fast test of the feasibility assumption above. It follows the fixture pattern already in `test/mcp/next-work.test.ts`: `initVault`, then `writeEvidence` three `transcript` records, then `computeNextWork`. Two of the records are `tool_error` permission denials from `Glob` that differ only in the path and session id. The third is the same kind of denial from `ost_check`. The spec should assert three things. The result carries a signature grouping next to `shown`/`total`/`hidden`. The two `Glob` records form one group with count 2 and `ost_check` has its own group. `fs` shows nothing new under `.ost-agent/` after the call.

**Pre-committed threshold:** at least 2 seeded records differing only in path and session id fall into exactly 1 group, and 0 records with different tool names share a group.

**What kind of red this is, stated plainly: `no-spec`.** The instrument tool refuses `-t "<name>"` filters because they contain shell punctuation. The only legal red instrument is a spec file that does not exist yet, so today's red is the weak kind and gives no build permit. The builder's first job is to write the spec described above and watch it fail on the missing grouping field (`computeNextWork` returns no such field today). Building the grouping comes after that. The assertion is written out here so the next reader doesn't get a blank file.

**What this does not settle.** A green run proves the groups are computed and stable on fixture data. It does not prove the live queue of 830 collapses to a handful of groups: that is a reading of the real store. It also says nothing about whether an operator acts from the groups, which is the sibling assumption and stays humans-required.

Unvalidated. Agent-proposed 2026-10-01; nobody has run it.
