---
type: Assumption
source: 'agent-ideation:2026-09-08-unattended-sweep'
created: '2026-09-08'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

**Risk category: viability** — specifically the operator's willingness to accept a permission posture, not whether the grant is technically possible.

The belief, stated so it could turn out false: *the operator, asked directly, will widen the harness's filesystem read grant to `/Users/tanner/dev/OST-Agent` and leave it open while unattended firings run.*

It could easily be false, and there is a reason to expect it might be. The grant has been refused on that exact path in at least eight captured records spanning 2026-08-06 to 2026-09-08, across many firings, while the same operator configured `product.repos` — opening the narrower MCP channel — some time before 2026-08-31. One channel was deliberately opened and the other was left shut. That is consistent with an operator who has already made this decision and made it the other way, and no pass has ever asked them.

Nothing else in this candidate matters if this is false: the candidate builds nothing, so the grant is the entire mechanism. That is why this is the assumption to test first and why it should be settled before either sibling is built — a supported verdict here retires two larger candidates for the price of one question.
