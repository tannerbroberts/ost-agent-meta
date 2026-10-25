---
type: AssumptionTest
source: 'REPO:test/adapters/transcript.test.ts'
created: '2026-10-25'
evidence: assertion
threshold: >-
  zero retry events for the listed signature across 3 calls, and exactly 1 retry
  for the argued repeat
instrument: npx vitest run test/adapters/transcript-prescribed-manifest.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.**

**What the spec should assert.** `test/adapters/transcript-prescribed-manifest.test.ts` reuses the fixture shape of `test/adapters/transcript.test.ts`. It gives the harvester a manifest listing `ost_ingest_inbox` and `ost_next_work` with input `{}`, in whatever form the builder chooses: a `TranscriptSourceOptions` field, or a file the source reads. The session holds:
- `ost_next_work` `{}` three times, which is a two-iteration firing's yield and so the count-independence case. **No** retry is filed for it.
- `Write` with the same full payload twice, the argument-carrying case this node's parent says must not be suppressed. **Exactly one** retry is filed for it.
- nothing matching the listed `ost_ingest_inbox` entry. The fetch result reports that entry as unmatched, which is the parent solution's claim that a stale manifest entry is visible.

**Pre-committed threshold:** zero retry events for the listed signature across three calls, exactly one retry for the argued repeat, and the unmatched entry named in the result.

**Which kind of red this is, honestly: `no-spec`.** The file does not exist, so today's red is the weak kind and grants no build permit. The instrument grammar admits only `npx vitest run <path>.test.ts`, and the existing transcript spec passes. What this node adds over a bare filename is the fixture and the three assertions above, plus the fact the build has to change: neither `TranscriptSourceOptions` nor `extractFriction` has anywhere to put a list today. Written as specified, it goes red on the first assertion against today's code, because all three `ost_next_work` calls after the first file as retries. That is when this test is finished.

**What this does NOT settle.** Whether the founder keeps the manifest current, which is the sibling viability test and humans-required on purpose and the risk this candidate actually stands or falls on. Green here means suppression is buildable and safe on the cases named, not that the list will stay true.
