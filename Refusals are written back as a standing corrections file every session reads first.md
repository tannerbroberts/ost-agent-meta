---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The corrections worth inheriting fit in a session's opening context]]

When a tool refuses a call and explains why, the correction is appended to a small durable corrections file scoped to this project. Every session reads it as part of its opening context. The lesson stops being something a session earns and becomes something a session inherits.

Entries are the refusal and its remedy, deduplicated, most-recent-first, with a count of how many times the refusal has been hit. The count is the useful part: it says which corrections are load-bearing and which were one-offs, and it is the number that would show whether the file is working at all.

**Compared to the alternatives.** Cheapest to build of any option here — it is an append and a read. It carries lessons across sessions, which an in-session repeat detector cannot, but it is strictly worse at the in-session case, because a correction only reaches the next session and the eleven-session blocked-sleep pattern shows repeats happening within one. The two are complements rather than rivals.

**What would make this the wrong pick.** It grows without bound and competes for the same opening context as everything else. A corrections file long enough to contain every lesson is one nobody reads, and there is no natural expiry: a refusal that stopped happening because the file fixed it looks identical to one that stopped mattering.

## Definition of done

"Draft the corrections file from past refusals and check whether it would have fitted in context"

```
npx vitest run test/knowledge/corrections-file-size.test.ts
```

Red today: nothing in the repository assembles refusals into a corrections file, so there is no length to measure. Green when the builder exists and the deduplicated file — plus each of the two candidate expiry rules — lands under 2,000 characters.

**What this does not settle.** Size is necessary and not sufficient. A green here says the file would fit in context; it says nothing about whether a session that has it actually applies it, which is the claim this solution really rests on. That half remains untested, and the evidence now on "The same refusal is rediscovered every session, because nothing carries the lesson forward" is why it matters: across eight captured sessions the correction was already delivered in full, at the moment of the error, and complied with — and still did not survive into the next session. A file that fits is not yet a file that is read.

## History
- 2026-08-05 unlinked "Draft the corrections file from past refusals and check whether it would have fitted in context" — moved under "The corrections worth inheriting fit in a session's opening context" — the belief this test measures now has a node of its own

## The mechanism appears in this pass's opening context — 2026-08-07

This node's Definition of done says "Red today: nothing in the repository assembles refusals into a corrections file, so there is no length to measure." That is no longer true of the context a pass receives, whatever turns out to be true of the repository.

**What arrived.** This pass's system prompt carries a block headed "CORRECTIONS ALREADY ISSUED IN THIS WORKSPACE (read before composing a call)", introduced as: "Each of these is a call the surface has already refused here, with the form it asked for instead. They were paid for once. Compose the permitted form the first time." It holds three entries. Each is a refusal, the form the surface asked for instead, the tool it was refused on, and a hit count written as "refused 1 time(s) (Bash)".

**That is this node's specification rather than something adjacent to it.** This body asked for "the refusal and its remedy, deduplicated, most-recent-first, with a count of how many times the refusal has been hit", and said "the count is the useful part: it says which corrections are load-bearing and which were one-offs". All four properties are present in the artifact, including the count.

**One of the three entries is the blocked sleep-then-poll.** That is the refusal the census on "The same refusal is rediscovered every session, because nothing carries the lesson forward" tracks across thirteen sessions and fifteen-plus occurrences — the single most repeated lesson this vault has recorded failing to carry. It is now carried, at least into this session.

**Against the size bar.** The test beneath "The corrections worth inheriting fit in a session's opening context" fixed 2,000 characters as the bar for whether such a file fits in opening context. The live block runs to roughly 700 characters at three entries, comfortably inside it. That is weak confirmation rather than strong: at three entries the file is not yet exercising the property the bar exists to catch, which is unbounded growth with no expiry rule. The bar becomes informative when the file is old, not when it is new.

**What this does not settle, and one half is the half that matters.** This node's own caveat stands untouched: "A file that fits is not yet a file that is read." This pass hit none of the three refusals the block names, which is consistent with having read and applied it and equally consistent with never having had occasion to make those calls — and the agent reporting that is the same agent whose compliance is the measurement. Separately, this pass cannot confirm what the Definition of done is actually about: whether *the repository* assembles this block. Product-directory reads were denied and `product.repos` is unconfigured, so the artifact is observed in the prompt and its producer is inferred. The neighbouring section in the same prompt is verbatim PR #69's shipped output, which makes `autonomous-pass.sh` the likely assembler — likely, not confirmed.

**For a human.** If OST-Agent does assemble this block, this solution's status is wrong and its instrument is unwriteable as specified: a spec asserting the assembler exists would be green on arrival and measure nothing. That is the same shape already recorded on "Refuse a wiki-link that contains a newline" and "Refuse a write whose content is empty or literally undefined", making this the third instance of the queue offering an instrument for behaviour that may already ship. Status deliberately left unchanged rather than set to `shipped` on an inference — the two siblings were promoted on the strength of their own prose, and this one would be promoted on the strength of a prompt block whose author this pass could not read.

_First-party observation by the unattended sweep of 2026-08-07, of its own opening context. Observed behaviour of this product's own agent: it grounds feasibility, not demand. No test was run and no result recorded._

## The file is in context, and one entry in it is not a lesson — unattended sweep, 2026-08-20

This pass's opening context carries the corrections block again, now with three entries, the first of them: `Read` refused because its input "could not be parsed as JSON", "refused 24 time(s) across 19 sessions". A text count over `.ost-agent/evidence/` this pass gives exactly 24 occurrences across 19 transcript records, so the block's counter is measuring the same thing the evidence store holds. The most recent occurrence is `TRANSCRIPT:1329bda4-c23b-427a-aeab-9536c1d87cf9` (2026-08-19), three times in one session. Whether that session had the block in its context is not recorded anywhere this pass can read, so this is not yet the "file in context, refusal still made" observation the node's own caveat asks for — it is the shape of one, waiting on a per-session record of what the block contained when the session started.

**The sharper point is about what the entry is.** A blocked `sleep` is a lesson: there is a constraint, a remedy, and a session that reads the remedy can comply. A `Read` call whose JSON has a stray comma is not a lesson — it is a generation slip, and the remedy ("retry with valid JSON") teaches nothing a session did not already know. Its count will therefore keep rising for as long as the harness rejects malformed input, and it sits at the head of the block by virtue of being the largest number in it. That is the no-expiry failure this node's "What would make this the wrong pick" predicted, arriving from an unexpected direction: not a correction that stopped mattering, but an entry that was never a correction. A builder extending the assembler should consider whether an entry whose remedy is "do what you meant to do" belongs in a file whose purpose is to carry remedies forward.

_First-party observation of this pass's own opening context plus a text count over the evidence store. Grounds feasibility and usability, not demand. No test run; rung unchanged._
