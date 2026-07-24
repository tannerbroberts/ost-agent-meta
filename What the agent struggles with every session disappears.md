---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-24-opp-transcript-ingestion.md'
created: '2026-07-24'
---
#Opportunity #unvalidated #needs-customer-interview
[[Post-session transcript harvester]]
[[In-the-moment friction events filed by the agent]]

**The need (customer's voice):** "The agent gets confused, asks the same question again, stalls on the same step — and all of that is thrown away when the session ends. The clearest usage data this product has ever produced is being deleted every day."

**Why it matters:** A subset of the evidence-famine need, addressing a channel that already exists and is currently discarded. The agent running the OST is the product's most active user; every question, uncertainty, retry, and stall it hits is *observed behavior* (non-founder, non-stated) about where the product is hard to use. Unlike recruiting outside users, this channel needs no one's permission.

**Litmus test:** More than one way — harvest transcripts into the inbox, emit structured friction events at the point of stall, have the agent file its own confusions, mine commit/tool-error history. Passes.

**Caveat for a human:** Dogfood friction is usage data about *one* user who is not a paying customer, so it grounds usability far better than it grounds demand. It should not be allowed to substitute for the outside-user evidence the parent opportunity is about.

Evidence: `INBOX:2026-07-24-opp-transcript-ingestion.md`
