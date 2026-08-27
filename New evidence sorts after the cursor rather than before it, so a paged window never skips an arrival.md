---
type: Assumption
source: 'agent-run:unattended-sweep-2026-08-27'
created: '2026-08-27'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

**The belief, stated so it could be false.** The queue that cursor pagination would be applied to is append-ordered under its sort key — an item captured after the cursor was issued sorts after it, and so is still reachable on a later page.

**Risk category: feasibility.** It is a claim about the data, checkable without asking anybody.

**Why it is the riskiest thing this candidate rests on, and why it is probably false.** The evidence ids visible in this pass's own sweep are `TRANSCRIPT:0095203e…`, `00c3120a…`, `01e55025…` — random UUIDs, not timestamps. A UUID captured tomorrow is equally likely to sort anywhere in the existing range, so roughly half of all new arrivals would land *before* any cursor already issued and would never be served again. That is strictly worse than the frozen window this branch exists to fix: today the tail is merely unread, whereas under a cursor half of new evidence would become unreachable, and unreachable silently. The list is sorted by id and the ids carry no time, which is the whole hazard in one sentence.

**What would make it true instead.** Sorting on capture time rather than id. The sweep already reports a `mirror` block per item with a `fetchedAt` field — presently `null` for 393 of 423 records, which is its own problem — so the monotonic key the convention needs is named in the response but not populated. If it were, the assumption holds; if it stays null, this candidate should be recorded as refuted on mechanism and the tree should prefer a sibling.

**What settles it.** Read the sort key actually used for `unmappedEvidence`, and check whether a record inserted after a page was served can sort before that page's last member.

**What a verdict here does not settle.** Nothing about whether pagination is the right shape, and nothing about the other two candidates. This is one mechanism check on one candidate.
