---
type: Assumption
source: 'TRANSCRIPT:28d14def-76a2-4bbb-bd55-6f9b80c8ca8c'
created: '2026-08-06'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Require every size-capped tool to answer a size probe without materialising its payload]]

**The belief, stated so it could be false.** The size of a response that might be refused can be reported without paying the cost of building that response, so a caller can plan around the limit instead of discovering it by exceeding it.

**Why it is the riskiest one.** For the two refusals this vault actually recorded, the answer runs opposite ways, and that is what makes it worth testing rather than assuming. A `Read` refused at 73,874 tokens against a 25,000 cap — session `28d14def` — is sized trivially: the file length is a stat call. But `ost_read_tree` returning 134,240 characters is only sized by walking 1,007 node files and serialising them, which is the entire cost of the operation. If the cheap probe does not exist for the tools whose limits actually bite, the solution degrades to "the refusal message states the size", which is a much smaller idea than the one written and does not let a caller plan *before* spending the turn.

**What class this is.** Feasibility. Answerable from the repository by construction — either a size can be computed without materialising the payload or it cannot, per tool.

**How it could come out false — usefully.** A middle answer is the likely one: sizes are cheap for file-backed reads and expensive for computed aggregations. That would split the solution into a real feature for one class and a documentation change for the other, which is a better outcome than shipping it as one thing.
