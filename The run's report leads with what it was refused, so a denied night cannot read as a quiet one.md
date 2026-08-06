---
type: Solution
status: unvalidated
source: 'TRANSCRIPT:8a9777ad-a1ca-47fc-ab8e-3bd4b001a5cd'
created: '2026-08-06'
evidence: observed
---
#Solution #unvalidated #evidence/observed
[[An operator handed a refusals section acts on it instead of learning to skip it]]

Leave the permissions exactly as they are and change what the morning looks like.

Right now an unattended pass reports what it did. Five sessions in the record did substantially less than they were asked to, because `ost_flag_humans_required`, `ost_check`, `ost_debt`, `ost_status` and `Glob` were each denied — and none of that reached the operator except as an absence. An absence and a completed sweep produce the same artefact: a tidy summary of some nodes that were written.

The proposal is that every refusal the run collects becomes the first section of its report, not a footnote: the tool that was denied, how many times, and the specific work item that was abandoned because of it. "I could not flag four tests as humans-required; here are the four" is a different message from silence, and it is a message the operator can act on in under a minute.

The bet is that the expensive failure here is not the missing capability but the missing signal. Operators tolerate a tool being unavailable; what they cannot tolerate is not knowing which of their nights were real. This solution is strictly weaker than preventing the gap and strictly cheaper — it needs no coordination with the permission system at all, only a counter and a section heading.

It also generalises past permissions, which the other two candidates do not. A run blocked by an unconfigured `product.repos`, a rate limit, or a spent lookup budget produces the same silent hole, and the same section would carry all of them. That breadth is the argument for building this one first even if a preflight follows.

The risk is that it becomes noise. A report that opens with a list of everything that did not happen, every morning, is a report that stops being read by the second week — which is the same failure mode the node "Three gates fired correctly in one session and every one of them read as noise first" already describes at the gate layer. Whether an operator actually acts on a refusals section is the assumption to probe, and it is not a question the repository can answer.
