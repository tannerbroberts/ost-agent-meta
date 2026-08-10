---
type: Solution
source: 'TRANSCRIPT:3b9eaea5-d098-4f47-ad0a-65871012d639'
created: '2026-08-10'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**The idea.** Fix it upstream, where the volume is manufactured. `adapters/transcript.ts` currently mints one evidence record per session. Instead, key a record on the *signature* of the friction — the tool name and the error class, e.g. `permission-denied:mcp__ost-agent__ost_check` — and keep one record per signature per window, whose body carries a count and the session ids it covers. Forty sessions denied the same tool become one record that says forty.

**Why upstream is a defensible place for this.** Nothing downstream can recover the fact that these forty are one event; it has to be inferred from bodies that were written independently. The adapter is the one place that sees the raw stream and knows the shape. It is also the only fix that shrinks the queue at rest rather than giving the operator a faster way to work through it.

**And it makes the record better, not just fewer.** A count is the datum. "This surface was denied `ost_check` on forty of the last sixty firings" is a stronger and more actionable statement than forty copies of "this surface was denied `ost_check`", and today that number exists nowhere — it is latent in a pile nobody totals.

**Contrast with siblings.** The other two act after storage and leave the operator holding the class. This one decides for them, which is the trade: less work, less choice. Against "a node may cite many sources", note they solve overlapping halves — that one lets a node point at forty records, this one means there is one record to point at. If both shipped, this would make that one much less necessary for transcripts specifically and no less necessary for inbox notes and webhooks.

**Where it fails, and it is the serious objection.** Rolling up is lossy and the loss is chosen by whoever writes the signature function. Two denials of the same tool in different contexts — one a misconfiguration, one a genuine capability gap — collapse into one record, and the distinction that mattered is gone before any reader sees it. The current one-record-per-session scheme is dumb but it is faithful, and faithfulness is what an evidence store is for. A window boundary adds a second arbitrary choice: an event straddling it appears twice with two partial counts.

There is also a migration question with no clean answer: the 85 transcript records already stored were written under the old scheme and this does nothing for them.

**Cost.** Medium, concentrated in the signature function, which is where all the judgement lives and which will be re-tuned repeatedly.

⚠️ Unvalidated. Agent-ideated.
