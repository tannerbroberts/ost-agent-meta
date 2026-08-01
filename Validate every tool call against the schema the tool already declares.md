---
type: Solution
source: 'agent-build:2026-07-26 v0.17.0'
created: '2026-07-26'
evidence: assertion
---
#Solution #evidence/assertion

**The idea.** Before a tool touches the vault, check the input against the JSON Schema the tool itself publishes — required properties present, no unexpected ones, types as declared — and refuse the call with a message naming the offending property. **Shipped in v0.17.0.**

**Why this was the cheapest thing that could work.** Every tool already declared a complete schema; nothing needed authoring. The schemas were being used to describe the tools to a model and to nobody else, so the information required to catch this had been sitting one function call away from the code that needed it. The fix is a validator over a six-keyword subset of JSON Schema and one call site.

**What it caught, verified rather than assumed.** The exact original call, replayed: `ost_annotate --input '{"title":"…","note":"…"}'` now answers *missing required property `issue`* and *unexpected property `note` — allowed: title, issue*, and writes nothing.

**Where it fails, and this is a real limit.** It checks *shape*, not *meaning*. A call with every field present and the right types, carrying the wrong node title or an empty string, still writes. It also cannot help a tool that ships without a usable schema — so a companion test asserts every allowlisted tool declares one, because a validator finding nothing to check reports the same "0 problems" as one that checked everything.

**Deliberately not done: repairing the fourteen damaged lines.** They are annotations in an append-only vault. Rewriting them would be the exact class of action this product refuses, and the notes they replaced are gone in any case.

## History
- 2026-08-01 evidence: observed → assertion — demoted by the fifteenth pass — B3's rung-unearned guard (v0.23.0-line) shipped after this node was authored; its source is not a TRANSCRIPT: recording, so 'observed' was unearned. Demotion only, per rungs.ts's own remedy.
