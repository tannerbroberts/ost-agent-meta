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

[[Draft the corrections file from past refusals and check whether it would have fitted in context]]

```
npx vitest run test/knowledge/corrections-file-size.test.ts
```

Red today: nothing in the repository assembles refusals into a corrections file, so there is no length to measure. Green when the builder exists and the deduplicated file — plus each of the two candidate expiry rules — lands under 2,000 characters.

**What this does not settle.** Size is necessary and not sufficient. A green here says the file would fit in context; it says nothing about whether a session that has it actually applies it, which is the claim this solution really rests on. That half remains untested, and the evidence now on [[The same refusal is rediscovered every session, because nothing carries the lesson forward]] is why it matters: across eight captured sessions the correction was already delivered in full, at the moment of the error, and complied with — and still did not survive into the next session. A file that fits is not yet a file that is read.

## History
- 2026-08-05 unlinked [[Draft the corrections file from past refusals and check whether it would have fitted in context]] — moved under [[The corrections worth inheriting fit in a session's opening context]] — the belief this test measures now has a node of its own
