---
type: Solution
source: 'TRANSCRIPT:3b9eaea5-d098-4f47-ad0a-65871012d639'
created: '2026-08-10'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[A signature can group the friction records without collapsing distinctions that matter]]

**The idea.** Fix it upstream, where the volume is manufactured. `adapters/transcript.ts` currently mints one evidence record per session. Instead, key a record on the *signature* of the friction — the tool name and the error class, e.g. `permission-denied:mcp__ost-agent__ost_check` — and keep one record per signature per window, whose body carries a count and the session ids it covers. Forty sessions denied the same tool become one record that says forty.

**Why upstream is a defensible place for this.** Nothing downstream can recover the fact that these forty are one event; it has to be inferred from bodies that were written independently. The adapter is the one place that sees the raw stream and knows the shape. It is also the only fix that shrinks the queue at rest rather than giving the operator a faster way to work through it.

**And it makes the record better, not just fewer.** A count is the datum. "This surface was denied `ost_check` on forty of the last sixty firings" is a stronger and more actionable statement than forty copies of "this surface was denied `ost_check`", and today that number exists nowhere — it is latent in a pile nobody totals.

**Contrast with siblings.** The other two act after storage and leave the operator holding the class. This one decides for them, which is the trade: less work, less choice. Against "a node may cite many sources", note they solve overlapping halves — that one lets a node point at forty records, this one means there is one record to point at. If both shipped, this would make that one much less necessary for transcripts specifically and no less necessary for inbox notes and webhooks.

**Where it fails, and it is the serious objection.** Rolling up is lossy and the loss is chosen by whoever writes the signature function. Two denials of the same tool in different contexts — one a misconfiguration, one a genuine capability gap — collapse into one record, and the distinction that mattered is gone before any reader sees it. The current one-record-per-session scheme is dumb but it is faithful, and faithfulness is what an evidence store is for. A window boundary adds a second arbitrary choice: an event straddling it appears twice with two partial counts.

There is also a migration question with no clean answer: the 85 transcript records already stored were written under the old scheme and this does nothing for them.

**Cost.** Medium, concentrated in the signature function, which is where all the judgement lives and which will be re-tuned repeatedly.

⚠️ Unvalidated. Agent-ideated.

## Definition of done

"Feed the signature two denials of one tool and two different error classes and require two groups not one"

```
npx vitest run test/adapters/transcript-rollup.test.ts
```

Quoted rather than linked: the test hangs under the Assumption "A signature can group the friction records without collapsing distinctions that matter".

Red today as **`no-spec`** — `adapters/transcript.ts` mints one record per session and there is no signature function to import. The separating assertion is the one to write first: a permission denial and an `InputValidationError` on the same tool must not merge, and both appear in one real stored session, so the fixture is transcribed rather than imagined.

## The latent number, totalled — first-party census of the stored corpus, 2026-08-28

This node's body says of the roll-up count: "today that number exists nowhere — it is latent in a pile nobody totals." This pass totalled it. The figures below are the datum the node argues for, measured rather than projected, and they are recorded here because this is the node they bear on.

**Corpus size, and how far it has moved.** The body's migration caveat reads "the 85 transcript records already stored were written under the old scheme." There are now **458** stored transcript evidence records, **434** of them still unmapped. The one-record-per-session scheme has produced a 5.4x growth in the pile since this candidate was written, and the migration question the node flagged as having no clean answer is now 5.4x larger than when it was flagged.

**Event volume.** 1,064 `tool_error` events across 391 records, and 729 `retry` events across 347 records — roughly 1,793 friction events distributed over 458 records.

**The shape distribution, which is the part that decides whether a signature function is worth writing.**

| Friction shape (literal match) | Events | Records | Share of corpus |
|---|---|---|---|
| read-before-write — "File has not been read yet" | 374 | 206 | 45% |
| permission denial — "but you haven't granted it yet" | 209 | 110 | 24% |
| blocked wait — "Blocked: sleep" | 35 | 32 | 7% |
| Read input parse — "could not be parsed as JSON" | 24 | 19 | 4% |

Those four shapes account for **642 of 1,064 tool errors — 60%** of everything the corpus records as a tool error. Record shares overlap and do not sum: a record carrying both a denial and a read-before-write is counted in both rows.

**What this settles, and it is the node's central bet.** The candidate rests on the claim that the volume is manufactured rather than real — that many records are one observation. Four literal strings covering 60% of all tool errors is that claim measured. The single largest shape alone, read-before-write, appears in 206 of 458 records: on the node's own proposal those 206 records become one record that says 206.

**What it does NOT settle, and this is the node's own serious objection, now with a number against it.** The 209 permission-denial events are the case the body warns about — "two denials of the same tool in different contexts collapse into one record, and the distinction that mattered is gone." That family is 24% of the corpus and is exactly where a careless signature would destroy meaning. The census counts shapes; it does not show that the shapes are the right grouping, and nothing here licenses the signature function's design.

**It also does not measure need.** These are the agent's own sessions. Per the standing evidence-class note carried on every transcript record, this grounds usability, not desirability, and must not be read as outside demand. The rung stays at the `assertion` floor and this pass did not move it.

**Method, so it can be rerun or disputed.** Literal substring counts with ripgrep over the 458 files in `.ost-agent/evidence/`, taken during the 2026-08-28 unattended sweep. No product code was executed and no test was run; this is a count of stored evidence bodies, which are themselves the adapter's per-session summary rather than a raw event stream, so the true event counts are at least these.

**Bearing on this node's own instrument.** Its definition of done requires a fixture whose strings are "transcribed rather than imagined," and specifically a permission denial and an input-parse error on the same tool that must not merge. Both families are confirmed present above at 209 and 24 events, so the fixture this instrument needs can be transcribed from the corpus rather than invented. The instrument itself was not touched by this pass.
