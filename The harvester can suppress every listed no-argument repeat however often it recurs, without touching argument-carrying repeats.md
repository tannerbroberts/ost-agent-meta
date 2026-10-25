---
type: Assumption
source: 'REPO:src/adapters/transcript.ts'
created: '2026-10-25'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion
[[A manifest-listed no-argument call repeated three times files nothing, an argued repeat still files, and an unmatched entry is reported]]

**Risk category: feasibility.**

**The belief, stated so it could be false:** a list a person edits can be matched against `extractFriction`'s signatures so that every repeat of a listed no-argument call (`ost_ingest_inbox:{}`, `ost_next_work:{}`) is suppressed, however many sweep iterations produced it. Argument-carrying repeats, which this node's standing finding names as genuine signal (`cf2cef94`, `09ec7cd2`), still file. And a listed entry that matched nothing in a harvest is reported rather than silently kept.

**Why this belief exists separately from the one beside it.** The sibling assumption "The founder will keep a manifest of prescribed call sequences current as the loop's steps change" is viability, and correctly humans-required. This node is the half a spec can settle. It is not trivial, for two reasons this node's own standing finding already recorded. A pair-shaped match under-suppresses multi-iteration firings, because the yield is `calls − 1` per argument-less tool. And the candidate's stated advantage over inference is that a stale entry is *visible*, which only holds if the harvester reports unmatched entries.

**What the repository says today (read 2026-10-25 via `ost_read_repo`).** `TranscriptSourceOptions` takes `dirs`, `quietMinutes`, `maxEventsPerSession` and `maxSessions`, and nothing that could carry a list. `extractFriction(jsonl)` takes the transcript text alone and pushes a `retry` on any second appearance of `name:input`. So the suppression has nowhere to be configured today.

**How it could be false.** The match may need more than a signature. If the loop's prescribed repeats ever carry arguments, for example a pass-specific cursor, a signature list cannot express them without also matching real repeats. The spec below covers the no-argument case only.

Unvalidated. Agent-surfaced 2026-10-25 by an unattended sweep; for a human to review.
