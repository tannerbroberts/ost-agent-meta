---
type: Solution
source: 'agent-run:unattended-sweep-2026-08-27'
created: '2026-08-27'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion

**Variation dimension: bought-vs-built. Position taken: the selection policy is adopted from outside unchanged; the only thing built here is the cursor store.**

Every capped list already has a stable ascending sort key and already reports its total. That is precisely the shape cursor pagination was designed for, and it is one of the most thoroughly worked-out conventions in software: the response carries an opaque `nextCursor` alongside `shown`/`total`/`hidden`, a caller that passes it back gets the next page, and a caller that omits it gets the head. The semantics, the failure modes, the operator's mental model and the wording of the contract are all borrowed as they are. This candidate writes no new rule about what a firing deserves to see.

**What is actually built.** One thing: somewhere for an unattended firing to keep the cursor between runs, since a scheduled firing has no session to hold it. The vault's `.ost-agent/` sidecar already persists per-run state and is the obvious home. That is the whole delta — the rest is a convention lifted intact.

**Why borrowing is the point rather than an economy.** The sibling candidates each invent a policy: one invents an operator-held window, the other invents a recency stamp. Inventing means owning the edge cases — what a window means when new items sort into the middle of it, whether an ignored item should really be stamped as seen. Cursor pagination's edge cases were settled by other people at scale, and adopting it means inheriting the answers instead of discovering them here, one firing at a time.

**What it gives up, and it is the sharpest give-up of the three.** A cursor assumes items are appended after the sort key it points at. This queue is not like that: evidence ids are random hex, so an item captured tomorrow can sort anywhere, and roughly half of new arrivals will land *before* the cursor and be skipped permanently. That is strictly worse than today for fresh evidence, which is the evidence most likely to matter. Borrowing the convention means also borrowing its assumption, and this queue violates it. Making it safe requires either a monotonic sort key (capture time, not id) or a periodic cursor reset — and at that point some of the policy is being built here after all, which weakens the candidate's own claim.

Ideated by an unattended pass on 2026-08-27 against the assigned dimension. Not blind: this surface holds no grant to run independent parallel ideators, so all three candidates under this opportunity were composed in one context by one author, which is the condition the blind-ideation rule exists to prevent. Read the three as one author's three answers, and discount their apparent distinctness accordingly.
