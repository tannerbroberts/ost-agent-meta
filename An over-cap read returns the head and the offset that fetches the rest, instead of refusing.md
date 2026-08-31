---
type: Solution
source: 'agent-ideation:2026-08-30-unattended-sweep'
created: '2026-08-31'
evidence: assertion
killIf: >-
  A month of transcripts shows a reader acting on a truncated body as if it were
  whole — citing or deciding from content that stopped mid-artifact — even once.
killBy: '2026-11-30'
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[A truncated read can name the offset that resumes it, and the resumed read returns the remainder with no gap or overlap]]

**Variation dimension: automated-vs-manual. Position taken: the truncation is automated and unconditional; what to do next stays entirely the reader's.**

A read that exceeds the cap never refuses. It returns the first cap's worth of content, `truncated: true`, the total size, and the offset a follow-up call would start at. The turn buys content rather than an error message, and the reader continues, stops, or asks for the next slice on its own judgement. Nothing is decided for it: the tool does not summarise, does not pick which part matters, and does not auto-paginate.

**Why this position and not another.** The failure is not that the artifact is large; it is that the turn produced nothing. Truncating converts a wasted turn into a partial one, which is the smallest change that removes the cost entirely. Automating the truncation and leaving the continuation manual is the split that matters: choosing *which* part of an artifact is worth reading is a judgement about the goal, and the tool does not know the goal.

**This is not speculative — half of it already ships here.** `src/product/repo.ts` does exactly this for file content: over `MAX_FILE_CHARS` it returns `redacted.slice(0, MAX_FILE_CHARS)` with `truncated: true` rather than throwing. The harness `Read` that produced this node's evidence does the opposite and refuses. So the candidate is: make the refusing readers behave like the truncating one, and add the offset the current form omits. `ost_read_tree` sits in between — it caps its listing and reports `shown`/`hidden`, but serves a node body whole.

**Against its siblings.** The listing-size candidate prevents the bad read; this one makes the bad read cheap. That difference matters most when the reader could not have consulted a listing at all — a node fetched by title, an id handed over by another tool — which is the majority of reads on this surface. It needs no per-entry stats and costs nothing until a cap is actually hit.

**What it gives up, plainly, and it is the dangerous direction.** Silent truncation is worse than refusal when it goes unnoticed. A refusal is impossible to mistake for success; a truncated body reads exactly like a whole one to anything that does not check the flag, and a reader that quotes the first 20,000 characters of a 40,000-character node and concludes from them has been misled rather than merely delayed. This repository already treats that risk as real — `src/product/repo.ts` frames the truncated text and sets the flag precisely so it can be checked — and the flag being present is not the same as it being read. This candidate converts a loud failure into a quiet one, and buys speed with that.

**What would make this the wrong pick.** If readers do not reliably check `truncated`, refusing is safer and this is a regression dressed as a convenience. The kill criterion above is aimed straight at that: one observed instance of deciding from a truncated body retires it.

**Honest note on how this was ideated.** All three candidates under this opportunity were composed in one context by one author; this surface holds no grant to run independent parallel ideators. Discount their apparent distinctness accordingly.

Unvalidated. Agent-ideated 2026-08-30; a human to review.
