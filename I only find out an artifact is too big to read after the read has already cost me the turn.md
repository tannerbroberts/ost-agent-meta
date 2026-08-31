---
type: Opportunity
source: 'TRANSCRIPT:d26678b6-e63d-4605-8d9d-f969fc8b466f'
created: '2026-08-31'
evidence: observed
authorship: machine
---
#Opportunity #unvalidated #evidence/observed

**The need, from the reader's side.** I decide what to read from a name and a listing. Neither carries a size. So the way I learn that a file or a node is larger than one read can take is to issue the read, spend the turn, and receive a refusal instead of the content — after which I still have to go back and ask again with an offset I am guessing at. The cost is paid before the information that would have avoided it arrives.

**The observation this is distilled from.** `TRANSCRIPT:d26678b6-e63d-4605-8d9d-f969fc8b466f`, an unattended firing of this vault with nobody watching, carries one genuine `tool_error`: a `Read` refused with "File content (29160 tokens) exceeds maximum allowed tokens (25000). Use offset and limit parameters to read specific portions of the file". The refusal names the remedy and arrives only once the request has already been made. Mechanically captured from the session transcript; it grounds usability, not desirability.

**Why this is a need rather than one tool's quirk, and it is first-party.** The same shape is in this product's own vault reader. `ost_read_tree` returns `proseChars` and a `truncated` array *with* the body — figures that describe the read after it has happened. The pass that distilled this node pulled one node body of 18,282 characters and another of 8,875, each time learning the size only by receiving it. So the reader that cannot size an artifact in advance is not only the harness's; it is the one this product ships.

**And the product already contains the counter-example, which is what makes this addressable rather than a complaint.** `src/product/repo.ts` gives `ost_read_repo` a `probe: true` mode that answers `bytes` and `wouldTruncate` from the `stat` the call takes anyway — no read, no redaction. Its own comment states the purpose in exactly the terms of this need: it is "the narrower call a caller who only wants to know whether a file is worth reading in full can make instead of discovering the cap by hitting it". One reader on this surface has the affordance; the others do not.

**Litmus test (more than one way to address this?):** Yes, and the candidates are genuinely different. Carry a size figure in the listing so no second call is needed. Add a probe mode to the readers that lack one, as `ost_read_repo` already has. Have an over-cap read return the head plus a stated remainder rather than refusing outright. Return the refusal with a usable offset already computed instead of advice to compute one. Passes — none of these is a rephrasing of another, and they differ on who pays the extra call.

**How this differs from its parent and from the node beside it.** The parent bucket is about compression — distilling a large thing into a smaller thing that preserves the decision. This is not that: knowing a file is 29,160 tokens compresses nothing and would have prevented this failure entirely. Torres's test against the parent's existing children, which are all compression primitives: a probe addresses this node and does nothing for fidelity-under-a-budget, and a distillation primitive addresses those and still cannot tell a caller the size before the call. Distinct.

**Duplication risk, stated because this pass could not rule it out.** The tree holds 162 opportunities and this surface has no way to search their titles; only the parent's own children were checked. If a node already states this need, merge this one into it rather than keeping both. What would settle it: a title search for "size", "probe", "truncate" or "too big" across the opportunity layer.

**What is not claimed.** One record, one signature. This says nothing about how often the failure occurs, and nothing about whether the cost is worth a build — the refusal is recoverable in one extra call, and a need that costs one turn occasionally is a different proposition from one that costs a turn every pass. Counting how many friction records in the queue carry a size-cap refusal is the cheap next step and was not done here.
