---
type: Solution
source: 'agent-build:2026-07-26 v0.17.0'
created: '2026-07-26'
evidence: assertion
---
#Solution #evidence/assertion
[[Sort a day of real failed calls into shape errors and meaning errors]]

**The idea.** Before a tool touches the vault, check the input against the JSON Schema the tool itself publishes — required properties present, no unexpected ones, types as declared — and refuse the call with a message naming the offending property. **Shipped in v0.17.0.**

**Why this was the cheapest thing that could work.** Every tool already declared a complete schema; nothing needed authoring. The schemas were being used to describe the tools to a model and to nobody else, so the information required to catch this had been sitting one function call away from the code that needed it. The fix is a validator over a six-keyword subset of JSON Schema and one call site.

**What it caught, verified rather than assumed.** The exact original call, replayed: `ost_annotate --input '{"title":"…","note":"…"}'` now answers *missing required property `issue`* and *unexpected property `note` — allowed: title, issue*, and writes nothing.

**Where it fails, and this is a real limit.** It checks *shape*, not *meaning*. A call with every field present and the right types, carrying the wrong node title or an empty string, still writes. It also cannot help a tool that ships without a usable schema — so a companion test asserts every allowlisted tool declares one, because a validator finding nothing to check reports the same "0 problems" as one that checked everything.

**Deliberately not done: repairing the fourteen damaged lines.** They are annotations in an append-only vault. Rewriting them would be the exact class of action this product refuses, and the notes they replaced are gone in any case.

## History
- 2026-08-01 evidence: observed → assertion — demoted by the fifteenth pass — B3's rung-unearned guard (v0.23.0-line) shipped after this node was authored; its source is not a TRANSCRIPT: recording, so 'observed' was unearned. Demotion only, per rungs.ts's own remedy.

## Definition of done

[[Sort a day of real failed calls into shape errors and meaning errors]]

```
npx vitest run test/telemetry/failure-shape-vs-meaning.test.ts
```

Red today: nothing classifies a recorded failure by kind — the trace stores the message and no code partitions it. Green when shape errors are shown to be at least half of all failures across 2026-07-25 to 2026-07-27, with probe calls reported separately rather than counted.

**This solution has already shipped, which makes the measurement more urgent rather than less.** v0.17.0 went out on the strength of one replayed call, so the coverage question has never been sized — and a validator that reports few problems reads identically whether it is catching everything or catching the easy tenth.

**What this does not settle.** The verdict stays a human's. And a green says the shipped validator is substantially complete for the failures that *have* happened; it does not say semantic damage is rare. A call with every field present and correctly typed, naming a node that does not exist, still writes — which is why a red here would send [[A tool call I got slightly wrong destroyed the note I was filing]] looking for a sibling aimed at meaning rather than shape.
